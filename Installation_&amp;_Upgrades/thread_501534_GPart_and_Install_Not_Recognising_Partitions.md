---
title: "GPart and Install Not Recognising Partitions"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by SimonM on 2007-07-15
Hello again,

I have been having a *ahem* little trouble trying to install ubuntu onto my desktop. Neither GParted or the installer recognise any of the current partitions, whilst I can browse both Windows and my soon-to-be shared area.

I tried to follow one of the threads about installing GRUB to see if that helps, the bash went like this:

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,6)
grub> root (hd0,6)
root (hd0,6)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

```

Ideas?

---

### Post by merlinus on 2007-07-15
Are you running from the live cd?  Have you installed ubuntu, or just grub?

How did you partition your drive?  What version of windows are you running?

Etc., etc.

-merlin

---

### Post by SimonM on 2007-07-15
Running for LiveCD
WinXP
...

90GB NTSF - Windows
30GB FAT32 - Shared
30GB ext3 - For Ubuntu

GRUB Failed to install as shown

---

### Post by merlinus on 2007-07-15
You may wish to check the live cd for errors.  You can do this from the boot-up menu.

Of you can download and use the alternate install cd, which is text-based.

-merlin

---

### Post by SimonM on 2007-07-16
There are no errors on the CD, downloading the alternative one now

---

### Post by SimonM on 2007-07-16
Thought I'd add a screenshot to help illustrate the problem :)

[IMG]http://farm2.static.flickr.com/1032/827224671_db2486a9fc_o.png[/IMG]

Also tried...

Suse, Gentoo and Kubuntu. All have exactly the same issues

---

