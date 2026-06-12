---
title: "[SOLVED] move from 64bit to 32bit"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by TC!! on 2008-08-14
I've installed Ubuntu on a spare computer to run XBMC, but I made the mistake of installing the 64 bit version which isn't supported. After trying to get things working (including using a 32 bit chroot) I've realised that the best way to run XBMC is to move to 32 bit heron.

Can you please tell me if there is any way for me to do this without destroying the home directories I've already setup? Please let me know any other information I need to give you.

The machine will mainly be used to run XBMC but I also run it as a local file server, svn repoistory and local DNS server.

---

### Post by TC!! on 2008-08-14
OK, looks like I've screwed my 64 bit installation by running envy in my 32 bit chroot!

I think my current installation has everything on one partition. What I was thinking is can i just install the 32 bit version of heron and ask it to create a new partition for itself and then use the home directories from my original installation by mounting them?

I got the idea from reading this, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome), which explains how to create a separate partition for home.

So I would do this:
1. Install 32 bit heron + ask it to use a new partition
2. delete everything apart from /home from my old partition
3. edit fstab to tell it to use the /home from my original partition

Does that sound possible? If I do this what is the minimum amount of space I need to install the system and can I tell Ubuntu how much space to use instead of just using all free space available?

---

### Post by TC!! on 2008-08-16
OK, now I really need help.

I did everything as I described above and now have system which is running 32 bit ubuntu and is still accessing my original /home from my original partition.

But things aren't running the way they should, it looks like there may be some permission problems with things accessing my files. First of all I don't get a bash history any more, my .bash_history file is always empty and whenever I open a new terminal I have no history. Next up I've been trying to run x11vnc and whenever someone tries to access the machine I see the error message that it couldn't read the password file which is in my home directory.

I've tried running chown -R username:username /home/username
That complains about permissions on .gvfs and doesn't seem to help at all.

Any help would be greatly appreciated.

---

### Post by kflorek on 2008-08-16
>Any help would be greatly appreciated.

 You evidently know much more about this sort of thing than I do because I'd consider this an impossible headache, but ...

  Its possible the 32 bit installer used a different ID number for you than what was used for the 64 bit install.The user name (which is associated with an ID number) is something the OS only keeps track of. The ID number is what is actually kept on the hard drive. I ran into this from installing many distros on the same HD and not being able to access my own files from a different OS because of supposed lack of permission.

 The other thing that gave me permission problems one time is temporary files in the /tmp directory. This happened after a crash in my case, but there were file name conficts from still existing left-overs that prevented the creation of some necessary temprorary files the OS or GUI is alway creating. The OS reported this error as insufficent permission.

---

### Post by TC!! on 2008-08-16
OK, I have found something out, the partition which holds my /home is reported as having no space available. If I try to create a new file like this:

echo test > test

I get "-bash: echo: write error: No space left on device", but if I do it with sudo then it works fine.

df -h reports this:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              21G  2.6G   18G  14% /
varrun                251M  104K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M   64K  251M   1% /dev
devshm                251M   12K  251M   1% /dev/shm
lrm                   251M   39M  213M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1             209G  202G     0 100% /home

That shows that there should be about 7G of space available, not 0.

I'm guessing that I have messed up how I mount my home directory, here is the line for it in my /etc/fstab:
/dev/sda1	/home	ext3	nodev,nosuid	0	2

This is driving me round the bend, what have I done wrong??

---

### Post by TC!! on 2008-08-18
Just wanted to post here to say that this has been cleared up in the other thread I posted about the issue:
[http://ubuntuforums.org/showthread.php?t=892396](http://ubuntuforums.org/showthread.php?t=892396)

In the end the problem was that about 5% of each disk is reserved for the root user to make sure you can't get yourself into big problems by filling your hard disk. The problem was that I managed to override that by using gparted to use 100% of the free disk space to create the new partition for my 32 bit installation. It kept telling me that I had no space available until I eventually deleted enough files to have more than the 5% reserved for root, that allowed my user to finally have some disk space available.

---

