---
title: "lubuntu 10.10 installer not starting,gui disappears"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by gijs007 on 2010-10-12
Hey guys im new to linux and these forums.

I was looking in to a easy to use linux distro to surf the internet, do some text editing and emailing for my moms old laptop, cause its being very slow with windows xp on it.

specs: intel pentium 4 2.4 ghz
256mb ddr ram
40 gb ide harddrive
nvidia geforce go 4 series gpu.(if I remember correct it is a **MX 440)**
brand medion

I figured out Lubuntu would be al right, so I connected my usb cd/dvd reader(cause intern cd/dvd drive is broken) put in a disc that I burned with my other pc and started up the os.

the live cd is working al right when its at the menu and I choose to start it it hangs for 30 sec-2 min
then it starts to load and eventually the desktop shows up then I can start to do things but as soon as I open something the gui disappears before the program opens.

I tried to run the installer but I get the same issue.
I see my mouse changing when I start the installer the mouse pointer doesn't points to the left side of the screen any more it points at the right side(which is strange)

I tested this on my other pc and the installer loads up just fine and everything works ok(though I still have the mouse pointer issue if I start the installer)

so can anybody help me with getting this issue fixed?


btw if you got any ideas for a better distro these are the requirements: my mom is a linux newbie so an easy to use, lightweight distro for internet browsing, emailing and text editing(word) is needed.
I think lubuntu will do?

btw2: is there any way to import settings from the windows os to the linux os?
btw3: dual boot should work just fine if I install this without deleting the windows partition right?

---

### Post by P4man on 2010-10-12
256 Mb is not enough for a live environment (and to be honest; not enough to run a recent ubuntu releases).

You might try installing with the alternate cd, but I would suggest trying a more leightweight alternative like lubuntu or peppermint:
[http://peppermintos.com/](http://peppermintos.com/)

Both are ubuntu based but you should work better on that hardware.

---

### Post by gijs007 on 2010-10-12
> **P4man said:**
> 256 Mb is not enough for a live environment (and to be honest; not enough to run a recent ubuntu releases).

You might try installing with the alternate cd, but I would suggest trying a more leightweight alternative like lubuntu or peppermint:
[http://peppermintos.com/](http://peppermintos.com/)

Both are ubuntu based but you should work better on that hardware.
thanks for your reply, but if you would have read my post you would have seen that im talking about **_Lubuntu. __not ubuntu._**

---

### Post by P4man on 2010-10-12
oops, sorry, my bad.
Still, even for lubuntu 256 Mb might be a tad low for a live environment , especially with no available swap.  But you could have a look at the output of ```
dmesg
``` to see if anything is acting up.

---

### Post by gijs007 on 2010-10-12
> **P4man said:**
> oops, sorry, my bad.
Still, even for lubuntu 256 Mb might be a tad low for a live environment , especially with no available swap.  But you could have a look at the output of ```
dmesg
``` to see if anything is acting up.
sorry im new to linux could you explain how to execute that command, I guess I have to look for a command prompt kind of application?

---

### Post by P4man on 2010-10-12
Yeah. Im not too familiar with lubuntu, but its in accessoiries > lxterminal it seems. Then enter dmesg and the screen will fill with a kernel log that may shed some light.

If you want to save the log to a file to upload it or post it here, enter

```
dmesg > log.txt
```

---

### Post by mörgæs on 2010-10-12
If your screen card is the problem, there might be some help here:
[http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)

---

### Post by gijs007 on 2010-10-13
> **P4man said:**
> Yeah. Im not too familiar with lubuntu, but its in accessoiries > lxterminal it seems. Then enter dmesg and the screen will fill with a kernel log that may shed some light.

If you want to save the log to a file to upload it or post it here, enter

```
dmesg > log.txt
```
where is the log file saved?

---

### Post by P4man on 2010-10-13
if you didnt change directories (and if you are unsure then you did not), then the file ought to be in your homefolder. If you want on it on your desktop do

```
dmesg > ~/Desktop/log.txt
```

(Im assuming LXDE uses the same conventions as gnome and kde.)

---

### Post by TinkerJ on 2010-10-17
I've confirmed with Lubuntu 10.10, that if I attempt install in a VM with 256MB RAM. The installer will not launch, and the LXDE taskbar process is killed.

Looks like available RAM gets so low that it starts randomly killing processes. It does seem to run with 384MB.

You may want to try some of the following distros for less than 384MB:
 [Peppermint]("http://peppermintos.com/")
 [Vector Linux]("http://www.vectorlinux.com/")
 [AntiX]("http://antix.mepis.org/index.php?title=Main_Page")
 [Zenwalk]("http://zenwalk.org/")

I've had some good experience with [TinyCore]("http://tinycorelinux.com/"), and you can install it to hard disk.

---

### Post by mörgæs on 2010-10-17
That is a very surprising result. I have Lubuntu 10.04 running on a machine (real, not virtual) with 192 MB.

Here are some more tests:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by P4man on 2010-10-17
> **mörgæs said:**
> That is a very surprising result. I have Lubuntu 10.04 running on a machine (real, not virtual) with 192 MB.

Here are some more tests:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

Its not so surprising. A live session requires a lot more ram, since it mounts a filesystem in ram. Im sure lubuntu etc will run with 256 Mb or even less if you install using the alternate cd, or on a machine that has a swap partition.

---

### Post by union two levers on 2010-10-17
hi, i am a newbie and am running linux mint 9 which is based on xubuntu 10.04 quite happily on a machine with 733mhz celeron processor and 256mhz memory..it is nice and easy to use.

---

### Post by mörgæs on 2010-10-17
@p4man:

I see, thanks.

---

### Post by gijs007 on 2010-10-22
> **TinkerJ said:**
> I've confirmed with Lubuntu 10.10, that if I attempt install in a VM with 256MB RAM. The installer will not launch, and the LXDE taskbar process is killed.

Looks like available RAM gets so low that it starts randomly killing processes. It does seem to run with 384MB.

You may want to try some of the following distros for less than 384MB:
 [Peppermint]("http://peppermintos.com/")
 [Vector Linux]("http://www.vectorlinux.com/")
 [AntiX]("http://antix.mepis.org/index.php?title=Main_Page")
 [Zenwalk]("http://zenwalk.org/")

I've had some good experience with [TinyCore]("http://tinycorelinux.com/"), and you can install it to hard disk.
thanks for testing:)
can someone tell me how to use the alternate install with a usb pendrive to install lubuntu next to windows xp?
btw: do I need to change party size etc or can the installer do this to and how do I do so?

---

### Post by mörgæs on 2010-10-22
It is not complicated.

1 Defragment Windows a couple of times. 
2 From Windows, shrink the existing partitions to give space for Ubuntu.
3 Follow these steps:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by gijs007 on 2010-10-23
aright I got the system running on lubuntu and its quite fast most of the time.
thanks for all the support.:)

---

### Post by Jared Norris on 2010-10-23
Just so you know for future there are 2 other options available that might be able to help you out.

Lubuntu now has both an alternate installer (text based so it's quicker and works on older hardware than the standard gui installer) and instructions for a minimal installation (which is also text based).

Alternate installation instructions & download link: [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall)

Minimal installation instructions & download link: [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

Hope that helps you in the future and anyone else reading this who might have the same problem.

---

