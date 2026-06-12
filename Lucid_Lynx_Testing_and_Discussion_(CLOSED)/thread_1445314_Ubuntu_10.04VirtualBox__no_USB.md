---
title: "Ubuntu 10.04/VirtualBox  no USB"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lochbroom on 2010-04-02
I have 10.04 installed on a VB and everything works fine except the USB ports, no trace when I plug in a Memory Stick. Can anyone help?

Thanks...John

---

### Post by Lollerke on 2010-04-02
Go into Users and groups, in the group options search for vboxusers and tick your username. Start VBox as superuser and USB works.

---

### Post by cariboo on 2010-04-02
I don't know if it has changed in Lucid, but in previous versions in order to use usb you need to install virtualbox from [here]("http://www.virtualbox.org/"), then install the guest additions.

---

### Post by Michaelg14 on 2010-04-02
In times past you had to insert this line in fstab

```
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0
```

With 10.04 I get the error message:
> mount: mount point /proc/bus/usb does not exist


and no USB is available in Vbox 3.1.6

Any thoughts?

---

### Post by quadomatic on 2010-04-03
I added that line to my /etc/fstab and then my system failed to boot...had to use a 6.04 LTS live cd to revert it.

So, USB not working in VirtualBox PUEL. The wiki says that virtualbox has built in usb support for lucid, and doesn't need usbfs which is deprecated, and that PUEL has changed direct handling of usb devices.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Lollerke on 2010-04-03
> **Michaelg14 said:**
> In times past you had to insert this line in fstab

```
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0
```

With 10.04 I get the error message:


and no USB is available in Vbox 3.1.6

Any thoughts?

Thats complicated. The easiest way: (VirtualBox must be downloaded from virtualbox.org and in the USB options you must add the device with Alt+Insert) Go into Users and groups, in the group options search for vboxusers,click on properties and tick your username. Start VBox as superuser and USB works if you installed the guest additions. [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---

### Post by quadomatic on 2010-04-04
None of the suggestions have been working...my user is ticked in vboxusers, mounting usbfs in fstab causes the computer not to boot, I tried executing this prior to vbox since it was suggested in a previous thread:

> hald --daemon=no

and that doesn't work either...any more ideas?

---

### Post by Michaelg14 on 2010-04-04
try starting VirtualBox using sudo VirtualBox in a terminal.  It should start as root, if you don't already have a virtual machine set up you can just us it as root.  If you have a machine you want to reuse close the root version and restart as you usually do.  USB will probably work.

---

### Post by Killigrew on 2010-04-04
do you have hal installed and running?

---

### Post by erkiha on 2010-04-04
Starting from lucid ubuntu does not run hal by default. Current releases of vbox (including 3.1.6) still require hal to discover host usb devices.

You need to run:

*sudo hald*

in terminal. NB!pay attention to run hald with sudo it can be run also without sudo but this does not help with usb devices

check with:

*ps -ef|grep hald*

if hal runs. If it doesn't you should get empty response for previous command.

Now start vbox (non ose version) and you have working USB devices. 

One other problem I have seen is missing permissions. You need to add your login user to vbox or similar group.

---

### Post by xebian on 2010-04-04
> **lochbroom said:**
> I have 10.04 installed on a VB and everything works fine except the USB ports, no trace when I plug in a Memory Stick. Can anyone help?

Thanks...John

It all depends on which version is your host.  The OSE (from the ubuntu repo) does not support it but the PULE from virtualbox.org does.

---

### Post by Whitby on 2010-04-05
I'll throw in my 2 cents worth on this one.

I was having the same problem - Lucid beta install with virtualbox downloaded from their website (so it is the one with USB support).  I wanted to try installing Windows 7 as a virtual machine, and use the USB support to update a GPS navigator which will only talk to windows (Boo!!!).

This just did not work.  I tried out the suggestions above one by one:

- went into users and groups and selected my user to be part of the vboxusers group
- went into the USB section of the selections for the virtual machine, located the USB device (which was certainly detected), and added a filter for it
- installed guest additions in the win7 VM (this didn't help)
- turned on IO APIC as detailed in the VirtualBox/USB documentation above (this installed OK in the VM, but didn't help with USB)
- tried running hald as sudo hald (this ran, but did not seem to make any difference)
- tried modifying fstab as used to be done for Karmic, and this rendered the system unbootable.  I had to use the Lucid live CD to get back in and undo this.
- tried running virtualbox as root (sudo VirtualBox).  This did start OK, but I had already spent some time setting up the virtual machine as a normal user, so I didn't want to go through it again.  I exited from this, went back to the win7 virtual machine and tested again.  USB still not working.

At this point, I was willing to try anything, and had a copy of Lubuntu 10.04 beta iso.  So I ran virtualbox as root again, and installed a Lubuntu virtual machine running as root.  I went into the selections for this machine, added a filter for the USB device, and BINGO! it worked.  I was then able to access any USB device I wanted in this VM just by adding a filter.  I did not install the guest additions in this VM.

Then, I exited this VM, and went back to the win7 VM as a normal user.  The USB then worked, and I was able to mount and access the GPS and other USB devices.  

I then completely deleted the Lubuntu machine installed as root, and did the same install again as the normal user.  USB worked in this VM by just adding filters, and did not need guest additions.

So, to cut a long story short, USB would not work until a virtual machine was installed as root and a USB device was configured there.  Once this was done, USB happily worked in VM's set up as a normal user, even after the root VM was deleted.  It is also not necessary to run hald, I am not running it for either of these VM's.

It looks as if there is something which needs to be set up in order to get USB support going, and this can only be done by root.  Once this is done, a normal user can use it.

Anyone else with a similar experience?

---

### Post by margazhang on 2010-04-07
I had similar problem with Linux Mint 8 (a variation of Ubuntu) on a HP computer. I solved the problem by UNcheck the "Enable USB 2.0 (EHCI) Controller" in the VirtualBox settings for USB. It worked without installing or login VB as root.

---

### Post by heepie on 2010-04-19
I follow the steps that Whitby mention a couple of reply above this one with the difference of using the virtualbox from the repositories and now I can't find a way to enable the USB as he mention through filters. So, my question is:

Do you actually need to have the one from the website to do this? Kinda silly question because he mentioned it, and I can't find an option on the repos version but I just wanted to make sure before I do the hole thing again...

ps - First time I tried Lubuntu and I'm very impressed...

---

### Post by recluce on 2010-04-19
I seem to have a similar problem. I am using Virtualbox 3.1.6 (Non-OSE) with Lucid x64 (all patches / kernel -21). hal is still installed on my machine - and after adding myself to the virtualbox usergroup, I was able to select my USB devices - except my 2 USB printers, which remained grayed out ("unavailable").

Using the "hald" command suggested in this thread did not make a difference, neither did disabling USB 2.0 support in VirtualBox. I was finally able to get my USB printers to be selectable (and working) by running VirtualBox as root ("sudo virtualbox").

Obviously, having to run Virtualbox as root is only a hack - for security reasons, VB really should not run with elevated privileges! So any idea why it takes root privileges on the Lucid host to print under VB 3.1.6? The same setup in Jaunty works just fine without elevated privileges!

BTW: the guest is Win XP SP3 32bit, even though I don't believe that matters for this issue.

---

### Post by heepie on 2010-04-19
That was unexpected...

After doing some reading and discovering that there were two different version of Virutabox (OSE and noneOSE). I went ahead and uinstalled virtualbox from my machine and installed the one from the website (noneOSE version).

Start it up after installation and to my surprise my old machine was still there... I only had to go and enable USB and VOALA!!! working out of the box, nothing else to be done....

---

### Post by Crunchy the Headcrab on 2010-04-19
> **heepie said:**
> That was unexpected...

After doing some reading and discovering that there were two different version of Virutabox (OSE and noneOSE). I went ahead and uinstalled virtualbox from my machine and installed the one from the website (noneOSE version).

Start it up after installation and to my surprise my old machine was still there... I only had to go and enable USB and VOALA!!! working out of the box, nothing else to be done....

Yeah virtual machines are great like that!  You can back them up on to a dvd or secondary drive and restore the whole thing if there's a problem.

---

### Post by Chenzo on 2010-04-19
I have virtualbox (non-free) working with usb in lucid.

Every time I run it, I run 'sudo hald' in terminal, then (this is important) I start virtualbox from the same terminal (VirtualBox).

I don't know if those expressing issues with starting hald first were running vbox from the terminal or not, but I was instructed to do it this way and it has worked ever since.

---

### Post by nanog on 2010-04-20
> 
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

If you have this line in your fstab you should remove it.

/proc/bus/usb no longer exists in lucid. usb devices are now handled by udev.

erkiha's temporary fix is the only solution until vbox updates for lucid (should happed shortly after release).

---

### Post by nanog on 2010-04-20
> then (this is important) I start virtualbox from the same terminal  (VirtualBox).

this should make no difference. you just need to make sure that you are not running vbox prior to running hal.

---

### Post by Whitby on 2010-04-20
This is getting a little confusing.

The gist of the replies above seems to be that all the features in VirtualBox work OK when it is run as root.  However, this has got to be a hack at best.  It doesn't seem a good idea to me to be running an application like this as root over an extended time, particularly if running a Windows guest OS which has the ability to connect to the internet.

I can only say again that my experience was that USB support worked when running as root, but I then found that it would work after that as a normal user.  I'm using VirtualBox as a normal user, just running from the menu and it's working properly.  I'm not now running anything as root, and not running hald.  I'm only using this for USB storage devices, I can't comment on USB printing as I don't have this.

---

### Post by artofsnow on 2010-04-23
Just to add my 2 cents ... I was running VirtualBox 3.1.6 PUEL on Ubuntu 9.10 64bit that I just upgraded to 10.04RC, haven't modified anything and USB is still working fine ;)

Edit: but I found that hald is running by default on my system

---

### Post by Bobhuber on 2010-04-23
With a fresh install of Lucid I also have no USB printer in VirtualBox (its there but greyed out. I've tried everything.
However as several users have posted I can run and install VirtualBox as root (gksudo) and the printer is available. Something is obviously not correct . I've been using VirtualBox in Karmic with no problems.

---

### Post by Whitby on 2010-04-25
A correction to the posts above.  When I said I wasn't running hald, it appears I was wrong.

It seems that when you run 'sudo hald', this spawns a number of processes related to hal.  I assumed that if I restarted the machine after this, that meant hald was not running after the machine came up again.  WRONG!!! I don't understand this, but the hald processes seem to come back again.  Doing 'ps -ef | grep hald' shows exactly the same processes after the reboot as before.  These processes do eventually go away, but how long this takes I'm not sure.

Sorry for misleading anyone about this, take note of the other posts saying that you do need to run 'sudo hald', because they are correct.

I only need to run hald as root, after this running VirtualBox as a normal user works OK with USB storage devices.

---

### Post by driftertx on 2010-04-29
[http://www.virtualbox.org/ticket/6343](http://www.virtualbox.org/ticket/6343)

known bug, will probably be fixed in a lucid version of virtualbox, temp work around is to run this before you start up your vb instance:

sudo hald --daemon=no

from command line, but has to be done each time you reboot your ubuntu box. 

hal was ripped out I believe from 10.04 and I think this spawns some legacy stuff to allow virtualbox/usbfs to function.

---

### Post by portis on 2010-04-29
Try virtualbox 3.2.0~beta1.
It works for me.

---

