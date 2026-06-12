---
title: "Upgraded 10.04 to 12.04 : horrible."
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by dave WB3DWE on 2014-10-01
Lost my gorgeous desktop. Gone are the icons along top. Gone is Python 3.1.1. In its place is a window with black window in the center. Does nothing. Only good thing is my programs are saved. Even the boot menu is changed ; now small. Started with 9.04 and spend hours tweaking 10.04. Since it wasn't broke I shouldn't have fixed. Is it possible to go back to 10.4 ?

---

### Post by sudodus on 2014-10-02
I'm sorry, upgrading to new versions is a one-way process. It is risky, so it is a good idea to backup the old system before starting. Otherwise there is no way back, if things go wrong.

On the other hand, Ubuntu desktop 10.04 LTS passed end of life in April 2013. The server packages are still supported, but the desktop specific program packages have received no security backups for one and a half year, so you need a new  version if you want to connect the computer to the internet with reasonable security. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

I hope that your personal files (documents, pictures etc) are saved alongside your programs, and I suggest that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") Depending on the hardware different versions and flavours of Ubuntu may be the best choice.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and you can get relevant advice what might work well.

---

### Post by dave WB3DWE on 2014-10-02
[FONT=lucida sans unicode][SIZE=3]Thanks for the comment.
My system is a seven-year-old Dell precision 390 with it's original Pentium 1.8 GHz processor, 4 GB memory and an NVIDIA
    256 MB video card, dual boot with XP. I'm at highest available video, 1440x900. A Cisco Linksys E3000 router hangs off a   cable modem.
I hope to upgrade to a core i3 system in a few months. If I stay with Linux I'll dual boot with Windows 7 Pro.
I assume I might as well advance the Ubuntu to 14 as my carefully tuned 10.04 is gone. My Python was not kept, so I'll install 3.2 or 3.3.
[/SIZE][/FONT]

---

### Post by sudodus on 2014-10-03
It is getting old, but it has workstation qualities, and I think you can get it to work well will a modern version and flavour of Ubuntu. As long as you have the P4 processor, I think it will be limiting the performance, and standard Ubuntu will not work well.

I suggest that you try ***Lubuntu 14.04.1 LTS (light-weight) or Xubuntu 14.04.1 LTS (medium-light-weight)*** depending on the kind of applications you want to run.

An alternative, that looks more like your old Ubuntu 10.04 is [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks") ***applied to Ubuntu 12.04 LTS***.

If you have problems with the graphics, please try to boot with the [boot option]("https://help.ubuntu.com/community/BootOptions") **nomodeset**, and then install a **proprietary nvidia graphics drive**r.

---

### Post by grahammechanical on 2014-10-03
What especially limits that machine for running Ubuntu is the 256 MB of video memory. Is it capable of hardware 3D rendering? This command will provide the answer

```
/usr/lib/nux/unity_support_test -p
```

Linux is still the OS to extend the life of old hardware but it also needs to provide the same quality video/graphic experience the rival operating systems are giving to their users. So, there comes a time when old graphic adapters are not capable of doing the job. So, we need to use flavours of Ubuntu that do not require so much from the graphic adapter.

There is also another issue. The makers of proprietary video drivers are in the habit of dropping support for the old graphic adapters from their latest drivers. And Ubuntu will install the latest proprietary video driver. You may need to find an older Nvidia driver for that graphic card. You might need to install Nvidia 173 or even 96.

Regards.

---

### Post by oldfred on 2014-10-03
I also liked the old menu system and my monitor is 4:3 so menu at top & bottom make better use than on side like Unity. 

So I installed fallback/flashback/gnome-panel. The name has changed in each version and the underlying software has also changed, but the look is very similar. Some things are in different places but that is less of an adjustment.

The link above to kansasnoob's install of fallback has lots of detail on settings. And that was most of what I followed.

       sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 

Some other links.
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

