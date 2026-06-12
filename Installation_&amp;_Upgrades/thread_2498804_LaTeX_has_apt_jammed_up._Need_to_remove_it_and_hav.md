---
title: "LaTeX has apt jammed up. Need to remove it and have not had any luck."
date: 2024-06-27
forum: Installation &amp; Upgrades
---

### Post by foxsquirrel on 2024-06-27
I have done this
```
fred@eng-dev2:~$ sudo killall -9 context mtxrun
context: no process found
mtxrun: no process found
fred@eng-dev2:~$ mtxrun --script cache --erase
mtx-cache       | writable path: /home/fred/.texlive2021/texmf-var/luatex-cache/context/b47c3d3cee7cb6c86268d0595268c442
mtx-cache       |
mtx-cache       |
mtx-cache       | total  :    0
mtx-cache       |
mtx-cache       | writable path: /home/fred/.texlive2021/texmf-var/luatex-cache/context/b47c3d3cee7cb6c86268d0595268c442
mtx-cache       |
mtx-cache       |

fred@eng-dev2:~$ sudo killall -9 context mtxrun
context: no process found
mtxrun: no process found
fred@eng-dev2:~$ sudo apt-get remove --purge context
E: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 6449 (dpkg)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
fred@eng-dev2:~$ sudo kill -9 6449
fred@eng-dev2:~$ sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
rm: cannot remove '/var/cache/apt/archives/lock': No such file or directory
fred@eng-dev2:~$ sudo apt-get remove --purge context
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
fred@eng-dev2:~$ sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
fred@eng-dev2:~$ sudo dpkg --configure -a
Setting up context (2021.03.05.20220211-1) ...
Running mtxrun --generate. This may take some time... done.
Pregenerating ConTeXt MarkIV format. This may take some time...
```

Any suggestions on how to stop this, I cannot break out of this.

---

### Post by currentshaft on 2024-07-02
Killing processes with SIGKILL (9) is how you likely ended up in this mess - stop doing that.

What happens if you have some patience and let "sudo dpkg --configure -a" finish what it's doing?

---

