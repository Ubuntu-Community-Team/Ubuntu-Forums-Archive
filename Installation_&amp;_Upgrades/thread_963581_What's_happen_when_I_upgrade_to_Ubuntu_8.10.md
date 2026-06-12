---
title: "What's happen when I upgrade to Ubuntu 8.10???"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by quangtrung1789 on 2008-10-30
This is my desktop after i upgrade Ubuntu 8.04 to 8.10 

[IMG][IMG]http://upnhanh.com/userimages/images/UpNhAnHdotC0M2008103030344ztk2mmjkmg567638.jpeg[/IMG][/IMG]

Can you help me???
Thanks.

---

### Post by quangtrung1789 on 2008-10-30
there's no anyone help :confused:???

---

### Post by revoman3 on 2008-10-30
Christ that must make you feel woozy, I have no idea how to fix that.
sorry, hope someone can help :)

---

### Post by Zorchenhimer on 2008-10-30
Looks like a video driver issue.  I've had this happen before.  Can't remember exactly how I fixed it.  One thing you should try is setting your resolution lower and reinstalling the video drivers.

---

### Post by quangtrung1789 on 2008-10-30
> **revoman3 said:**
> Christ that must make you feel woozy, I have no idea how to fix that.
sorry, hope someone can help :)
oh my god:)
i hope there will be someone can help me.

---

### Post by agathian on 2008-10-30
how does the non-graphical command line interface look?
try Ctrl-Alt-F1 [f2, f3, etc]

If that also has similar problems - this is most probably monitor or graphics card issue. 

If that is fine, then probably related to driver issue.. which needs to be debugged further

Just my $0.02

---

### Post by quangtrung1789 on 2008-10-30
> **agathian said:**
> how does the non-graphical command line interface look?
try Ctrl-Alt-F1 [f2, f3, etc]

If that also has similar problems - this is most probably monitor or graphics card issue. 

If that is fine, then probably related to driver issue.. which needs to be debugged further

Just my $0.02

can you show more somethings for me???
i only start use ubuntu in 2 month ago so that i don't really understand it yet.
thanks you.

---

### Post by quangtrung1789 on 2008-10-30
please, can you help me????:)

---

### Post by agathian on 2008-10-30
When you are at the login screen try pressing all these three keys together - Control [ctrl], Alt and F1

it should give you a non-graphical, command line, login screen.

If the flickering exists there also, then "my guess" would be that it is either a monitor or graphics card problem. In that case you might want to try and connect the monitor to another PC or laptop and double check as well.

If it doesnt flicker there - then it is probably a graphics driver problem. Which will require further debugging. you should probably search the forums for the type of your graphics card.. 

you can login thru that command line and run the command "lspci" and look for your video card.

---

### Post by quangtrung1789 on 2008-10-31
> **agathian said:**
> When you are at the login screen try pressing all these three keys together - Control [ctrl], Alt and F1

it should give you a non-graphical, command line, login screen.

If the flickering exists there also, then "my guess" would be that it is either a monitor or graphics card problem. In that case you might want to try and connect the monitor to another PC or laptop and double check as well.

If it doesnt flicker there - then it is probably a graphics driver problem. Which will require further debugging. you should probably search the forums for the type of your graphics card.. 

you can login thru that command line and run the command "lspci" and look for your video card.

This is the result when i run the command "lspci":(

> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


can you tell me about how to install driver for this video card???:)
Thanks.

---

### Post by quangtrung1789 on 2008-10-31
can you help me???:confused:

---

### Post by necrolin on 2008-10-31
Your screen in misconfigured. All you need to do is to configure it properly.

a) Like the others said press: alt+ctrl+F2 (any of the first 6 function keys will do)
b) You'll be in a text login screen and you'll need to login.
c) I believe that the command that you'll need to enter is: 
sudo dpkg-reconfigure xserver-xorg

I don't swear to this command because I'm not using Ubuntu right now. You can double check the exact command though very easily. It's in the first few lines of the file "/etc/X11/xorg.conf".  You can double check by typing "head /etc/X11/xorg.conf". This command will display the first few lines of the file xorg.conf on your screen.

d) Select the appropriate settings for your monitor and video card and you should be done. Reboot and see what happens.

---

### Post by agathian on 2008-10-31
quangtrung1789,

So i assume you are able to login to command line and there were no flickering there?

Try reconfiguring as "necrolin" has suggested, and let us know if it solves your issue.

Can you also run this comamnd "lshw -C display".. it should give more information on the driver it is using..

Good Luck.

---

### Post by n6yga on 2008-10-31
The command, as listed in my xorg.conf is:

sudo dpkg-reconfigure -phigh xserver-xorg

Hope this helps...

Mark.

---

