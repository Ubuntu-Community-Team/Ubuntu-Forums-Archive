---
title: "grub install problem"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by Anolis on 2008-10-18
So last night I decided to install Windows XP Pro. so that I could play spore without having graphics glitches. The only problem is that when I try to reinstall grub onto hd0,0 using the 8.04 and 8.10 beta install cd, it cannot detect the harddisk. Typing "root (hd0,0)" into the grub terminal returns:

> Error 21: Selected disk does not exist

I've done it before and it worked fine. What am I doing wrong? What information do I need to give to help you help me better?

>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> 


this is the output of dmesg [http://pastebin.ubuntu.com/59426/]("http://pastebin.ubuntu.com/59426/")

Ubuntu is installed on /dev/sda1, 
Windows is installed on /dev/sda2, 
swap is on /dev/sda5 in an extended partition located on /dev/sda3

[IMG]http://img505.imageshack.us/img505/420/screenshotdevsdagpartedoe3.png[/IMG]

---

### Post by caljohnsmith on 2008-10-18
Are you entering the Grub command line as root user? 
```
sudo grub
```

---

### Post by Anolis on 2008-10-19
I am now... I feel a bit absent minded now haha

thanks :)

That fixed the problem, can't believe i forgot about that

---

