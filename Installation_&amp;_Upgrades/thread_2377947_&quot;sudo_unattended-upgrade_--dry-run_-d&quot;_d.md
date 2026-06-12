---
title: "&quot;sudo unattended-upgrade --dry-run -d&quot; download packages?"
date: 2017-11-18
forum: Installation &amp; Upgrades
---

### Post by photonxp on 2017-11-18
I've got the answer. "unattended-upgrade --dry-run" do download packages.

unattended-upgrades --help
      --dry-run             Simulation, download but do not install
====================================
Just run the command "sudo unattended-upgrade --dry-run -d" and found out it downloaded packages from the Ubuntu mirror site. 
Is that the right behaviour?

```
man unattended-upgrade
```
>  --dry-run
                          Just simulate installing updates, do not actually do it

I also tried 
```
sudo apt-get upgrade --dry-run
```
 which didn't download packages at all.

Could anyone do the favour to reduplicate my procedure to verify or negate the result? 
Right now I don't have any other Ubuntu pc or virtual machine available.
You'd better backup your system and data before you try.

Here is my procedure:

```
lsb_release -a
```
> No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.1 LTS
Release: 16.04
Codename: xenial

```
uname -a
```
> Linux ub 4.4.0-98-generic #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```
sudo unattended-upgrade --dry-run -d
```

> ... ...
wget
wpasupplicant
xserver-common
xserver-xorg-core
xul-ext-ubufox
Get:1 [http://mirrors.duke.edu/ubuntu](http://mirrors.duke.edu/ubuntu) xenial-updates/main amd64 libreoffice-core amd64 1:5.1.6~rc2-0ubuntu1~xenial2 [28.2 MB]
54% [1 libreoffice-core 18.6 MB/28.2 MB 66%] 

```
Ctrl + C
``` 
to Interrupt the process:

> ... ...
wget
wpasupplicant
xserver-common
xserver-xorg-core
xul-ext-ubufox
Get:1 [http://mirrors.duke.edu/ubuntu](http://mirrors.duke.edu/ubuntu) xenial-updates/main amd64 libreoffice-core amd64 1:5.1.6~rc2-0ubuntu1~xenial2 [28.2 MB]
54% [1 libreoffice-core 18.8 MB/28.2 MB 66%] 16.5 kB/s 2h 4min 38s^CError in function stop
Traceback (most recent call last):
File "/usr/lib/python3/dist-packages/apt/progress/text.py", line 233, in stop
def stop(self):
KeyboardInterrupt
Traceback (most recent call last):
File "/usr/bin/unattended-upgrade", line 1468, in <module>
main(options)
File "/usr/bin/unattended-upgrade", line 1243, in main
res = fetcher.run()
SystemError: E:Method http has died unexpectedly!, E:Sub-process http returned an error code (100)

Is this download behaviour a bug or not?

---

### Post by photonxp on 2017-11-18
Upgrade packages of apt apt-utils libapt-pkg5.0 unattended-upgrades, 
then "sudo unattended-upgrade --dry-run -d" 

Still download packages from Ubuntu mirror site.
-------------------------------------------------------------------------------
Problem Solved.

---

