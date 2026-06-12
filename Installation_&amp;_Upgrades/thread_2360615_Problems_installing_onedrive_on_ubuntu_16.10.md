---
title: "Problems installing onedrive on ubuntu 16.10"
date: 2017-05-06
forum: Installation &amp; Upgrades
---

### Post by alejandrofig on 2017-05-06
Hello everyone, I have been trying to install onedrive on my ubuntu with no success. I followed both this tutorials( [https://www.youtube.com/watch?v=I66zXL8ZvAk](https://www.youtube.com/watch?v=I66zXL8ZvAk) , [https://www.youtube.com/watch?v=I66zXL8ZvAk](https://www.youtube.com/watch?v=I66zXL8ZvAk) ), and everything seems to work fine till the point i try to start onedrive typing in the terminal onedrive-d start and i get this:

Traceback (most recent call last):
  File "/usr/local/bin/onedrive-d", line 11, in <module>
    load_entry_point('onedrive-d==1.1.0.dev0', 'console_scripts', 'onedrive-d')()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 565, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2589, in load_entry_point
    return ep.load()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2249, in load
    return self.resolve()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2255, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/usr/local/lib/python3.5/dist-packages/onedrive_d-1.1.0.dev0-py3.5.egg/onedrive_d/od_main.py", line 9, in <module>
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/usr/local/lib/python3.5/dist-packages/daemonocle-1.0.1-py3.5.egg/daemonocle/__init__.py", line 9, in <module>
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/usr/local/lib/python3.5/dist-packages/daemonocle-1.0.1-py3.5.egg/daemonocle/cli.py", line 8, in <module>
AttributeError: module 'click' has no attribute 'MultiCommand'

I have no idea what is it about. Can anyone give me a hand? Thanks

---

### Post by alejandrofig on 2017-05-06
Solved, no problem, i had to install pip3 using the following comand :

sudo apt install python-pip

And everything worked fine.

---

### Post by changi22 on 2017-07-16
Both the YouTube videos are now removed. Can you please share the steps you followed?

---

### Post by christiancac on 2017-12-26
Did you find the solution? Everything installed for me but i do not see the directory or pop up window

---

### Post by christiancac on 2017-12-26
I used the [https://www.maketecheasier.com/sync-onedrive-linux/](https://www.maketecheasier.com/sync-onedrive-linux/)   Howver i am stuck at the install option when i do a ls i see  install.sh LICENSE in white and onedrive_d, read.md and setup.py what am i to run or install ?

---

