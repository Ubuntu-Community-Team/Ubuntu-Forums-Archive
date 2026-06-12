---
title: "Terminal doesn't open in Ubuntu 18.04"
date: 2020-01-18
forum: Installation &amp; Upgrades
---

### Post by hannzo96 on 2020-01-18
I was recently updating python version and PyQt5 then my terminal shut down and doesn't open anymore, it just shows the loading circle but it does not open whatsoever 
I tried googling and trying out solutions but nothing seems to work and the information are so outdated

---

### Post by guiverc on 2020-01-18
What did you do with python?  (specifically), and what do you get with `python -V; python3 -V`? 

The GUI terminal, along with a number of Ubuntu tools, rely on python3 being a specific version, so changing defaults can cause those tools to no longer work as expected.  Text terminals should still work (eg. ctrl+alt+F4)

---

### Post by hannzo96 on 2020-01-18
hi i tried using tty terminal and checked python version, it says 2.7.17, which is strange cuz i updated it to 3.7.1
i just want to know how to restore defaults and i want to update python version without having this issue again cuz i need to download a specific software

---

### Post by Impavidus on 2020-01-18
Ubuntu 18.04 comes with both python 2.7 and python 3.6. There are some tools that aren't specific about the python version they need and they need python 2, so just calling python will run python 2. If you want python 3, call it as python3.

On Ubuntu 19.10 all those tools have been updated and now run with python 3. Python 2 is no longer installed by default.

We can only tell you how to fix this if you can tell us how you tried to upgrade python.

---

### Post by hannzo96 on 2020-01-18
okay thanks for your reply, I wanted to install a live voice changer on ubuntu, i followed this guide on github and followed all instructions, my problem occured when i wrote the command for PyQt5 as far as i can remember
[https://github.com/juancarlospaco/pyvoicechanger](https://github.com/juancarlospaco/pyvoicechanger)

---

### Post by gypearce on 2020-01-18
I just did the same thing, I upgraded from Python 3.6 to Python 3.7. My current version is 3.7. Here are the commands I used:
python3 - - version (it was 3.6.9)
sudo apt update  - y
sudo apt install python3. 7
sudo update-alternatives  - - install /usr/bin/python3 python3 /user/bin/python3.6 1
sudo update-alternatives  - - install /usr/bin/python3 python3 /user/bin/python3.7 2
sudo update-alternatives   - - config python3 (I chose the #2 option which was python 3.7)

Wonder if I ran the last three commands again I would get my terminal back?

---

### Post by gypearce on 2020-01-18
NO, only run:
sudo update-alternatives  - - config python3
And choose option #1 and revert back to Python 3.6.
My terminal is back!! Hot stuff. 
So can someone show hannoz96 and I how to upgrade without breaking something! 
Thanks.

---

