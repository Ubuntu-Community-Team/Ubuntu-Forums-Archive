---
title: "Upgrading from 5.10 without cd"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by qubodup on 2007-09-02
Hi, I just installed ubuntu 5.10 from an old cd and of course would prefer to have 7.whatever on the system, cd burning abilities are veery limited arround here atm, so I want to either upgrade the system or install via http/ftp (which I did with FreeBSD once) I found [http://ubuntuforums.org/showthread.php?t=92265](http://ubuntuforums.org/showthread.php?t=92265) but...
```
root@localhost:~# apt-get update
Reading package lists... Done
root@localhost:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@localhost:~# 


```

Any ideas? I also read on some forum I should create a disk error (take out disk?) while in stage 1 and tell the installer to make a net install.. There were no stages I noticed and taking out the disc didn't give me any options..

Regards, qubodup

---

### Post by Pumalite on 2007-09-02
gksu "update-manager -c" it might work

---

### Post by qubodup on 2007-09-02
> **Pumalite said:**
> gksu "update-manager -c" it might work

It seems not to work, my system is up to date, but I can't upgrade, as it's not supported

---

### Post by Pumalite on 2007-09-02
Sorry. Someone else might have a better idea. I started using Ubuntu with 7.04

---

### Post by merlinus on 2007-09-02
IIRC 5.10 has not been supported for some time, so a dist-upgrade will not work.

-merlin

---

### Post by qubodup on 2007-09-02
> **merlinus said:**
> IIRC 5.10 has not been supported for some time, so a dist-upgrade will not work.

-merlin

Is there an option to install via network using my old cd or even using no cd at all?

---

### Post by Pumalite on 2007-09-02
Network Install

For those people using a Windows machine as the source for a network install, it can be done. Hopefully below will help someone one day with this exact scenario.

1 - Use TFTP.exe to serve as a network boot DHCP (instructions at this post) - [http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)

2 - Disable IIS (temporarily) - IIS has problems with some of the file name and file structures

3 - Extract the ISO to a folder on your harddrive (approx 7.5GB of space needed)

3 - Install Apache HTTP, edit the http.conf file change the "Document Root" (line 149) to the folder on your harddrive where you extracted Ubuntu and also change line 177 to the same directory. Do not use backslashes eg. c:\ubuntu must be in the http.conf file as c:/ubuntu

4 - Around line 203 of the http.conf file add "Allow from x.x.x.x" where XXX is the IP address of the computer you are installing from. OR (but be careful) you can say "Allow from all"

5 - Check that you can access this in your browser. (depends on how you config'd your apache)

5 - Then start TFTP.exe

6 - Set the remote machine to boot from network (check in your bios settings)

7 - It should boot from network and start installing.

A couple of posts that helped me out (which may help someone else in turn one day):
-----------------------------------------------------------------------------------
[https://help.ubuntu.com/community/In...sServerNetboot](https://help.ubuntu.com/community/In...sServerNetboot)
[http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)
[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)
[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)

---

### Post by qubodup on 2007-09-02
> **Pumalite said:**
> Network Install

,,,

Thanks for the effort, but I have no win machine at my avail.

Oh, I actually was refering to the web, so rather a http/ftp install than a network one.

I'll try to find something on installing linux using grub (I did such a thing once, but using an automatic installer for windows..) after all I can still dl and unpack the ubuntu 7 iso

---

### Post by Pumalite on 2007-09-02
[https://help.ubuntu.com/community/Installation#head-b751f1c9b3b4e0c27d6bc8828a831de92eb57a70](https://help.ubuntu.com/community/Installation#head-b751f1c9b3b4e0c27d6bc8828a831de92eb57a70)

---

### Post by qubodup on 2007-09-02
> **Pumalite said:**
> [https://help.ubuntu.com/community/Installation#head-b751f1c9b3b4e0c27d6bc8828a831de92eb57a70](https://help.ubuntu.com/community/Installation#head-b751f1c9b3b4e0c27d6bc8828a831de92eb57a70)

I found [http://www.bobpeers.com/linux/hard_drive_install](http://www.bobpeers.com/linux/hard_drive_install) and decided to  see if the ubuntu iso contains similar files, but  your link solves everything!

Thx man, will report back after the install!

---

### Post by Pumalite on 2007-09-02
You are welcome. Glad it worked for you!

---

### Post by qubodup on 2007-09-02
Freaky, a operational system installer that asks as good as nothing! (I'm used to FreeBSD and OpenSUSE - They won't install X without you wanting it)

I hope I'll enjoy ubuntu. Thanks for the help again, Pumalite!

---

