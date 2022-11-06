# min_heap_py

````py
class MinHeap:
    def __init__(self, arr):
        self.arr = arr
        self.n = len(arr)

    def insert(self, value):
        self.arr.append(value)
        self.n += 1
        self.heapify_up(self.n - 1)

    def delete(self):
        self.arr[0], self.arr[self.n - 1] = self.arr[self.n - 1], self.arr[0]
        self.arr.pop()
        self.n -= 1
        self.heapify_down(0)

    def heapify_down(self, i):
        lc, rc = i * 2 + 1, i * 2 + 2
        smallestValue, smallestIndex = self.arr[i], i
        if lc < self.n and self.arr[lc] < smallestValue:
            smallestValue, smallestIndex = self.arr[lc], lc
        if rc < self.n and self.arr[rc] < smallestValue:
            smallestValue, smallestIndex = self.arr[rc], rc
        if smallestIndex != i:
            self.arr[i], self.arr[smallestIndex] = self.arr[smallestIndex], self.arr[i]
            self.heapify_down(smallestIndex)

    def heapify_up(self, i):
        parent = (i - 1) // 2
        if parent >= 0 and self.arr[i] < self.arr[parent]:
            self.arr[i], self.arr[parent] = self.arr[parent], self.arr[i]
            self.heapify_up(parent)

    def buildHeap(self):
        last_non_leaf = self.n // 2 - 1
        for i in range(last_non_leaf, -1, -1):
            self.heapify_down(i)

    def get_min(self):
        return self.arr[0]




# # insert
# heap = MinHeap([110, 120, 130, 140, 150])
# heap.insert(115)
# heap.insert(120)
# heap.insert(130)
# heap.insert(160)
# print(heap.arr)
#
# # delete
# heap = MinHeap([110, 140, 150, 160, 170, 180])
# heap.delete()
# print(heap.arr)
#
# # build heap
# heap = MinHeap([90, 80, 70, 60, 50, 40, 30])
# heap.buildHeap()
# print(heap.arr)


heap = MinHeap([90, 80, 70, 60, 50, 40, 30])
heap.heapsort()
print(heap.arr)
print('--end--')
````
