---
title: "No signal from monitor during install"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Zeophlite on 2010-05-23
So my computer works reasonably fast running XP (old 3GHz processor with 512RAM), but every so often it simply freezes.  I've tried all I can to fix this, but sometimes when I boot up XP it'll get to the window's logo then freeze, sometimes it'll get all the way to the desktop and then freeze, and sometimes it'll start up, run fine for an hour or two then freeze.  By freeze, I mean the screen doesn't update, the keyboard and mouse do nothing.  Updating NVIDIA drivers doesn't seem to help - some make it worse!

So I've had enough, and decided to download Wubi to try Ubuntu on it.  I'm not ready to remove windows just yet (lots of data on this machine) and so I don't really want to try dual-booting yet.

Wubi downloads and runs in Windows fine.  When I go to restart, after picking Ubuntu from the menu it shows a little text (I think about installation, and press Esc for menu) then my monitor gives a "No Signal" message.

So I try restarting (pressing the button), and pressing Esc to bring up the menu.  I tried all 5ish options, and "Safe graphics mode" and "ACPI workarounds" seem to last longer, but the same error occurs, before it has even prompted me (still doing its own thing).

So I can get up to GRUB, and even get into the grub> prompt.  I tried adding irqpoll and/or all_generic_ide to the boot thing (pressing e in the grub menu), but that hasn't helped.

I'm unsure of how to find what hardware my computer has (only computer, don't have receipt), but I know "NVIDIA GeForce 6600 GT".

---

### Post by Zeophlite on 2010-05-31
Can't anyone suggest anything?  I just tried reinstalling Wubi, but that didn't help - same problem.
If anyone could even suggest how I might find out what model motherboard (and rest of my components) on Windows, then I could post them.

---

### Post by Zeophlite on 2010-06-02
bumpity bump

---

### Post by Yankeefan984 on 2010-06-02
Do you by any chance have an ATI video card?

---

### Post by Zeophlite on 2010-06-02
No, a NVIDIA GeForce 6600 GT

FMI, are there problems with ATI video cards?

---

### Post by oldfred on 2010-06-03
I have a newer nvidia 9600 and had to do this:

boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by Zeophlite on 2010-06-03
Yes that helped.  I rebooted, hit Esc, got the menu and choose normal, replaced "quiet splash" with "nomodeset", it opened up into a graphical install thing, installed Ubuntu and rebooted, came up into a new menu, which had Ubuntu (generic), which gave No Signal.  But by trying again, highlighting Ubuntu (generic) and hitting e, I could again replace "quiet splash" with "nomodeset" and get into a command line interface.

Running gksudo nvidia-settings gives:
(gksudo:992): Gtk-WARNING **: cannot open display:
and that's it!

So how do I get the desktop working now?

Thanks for your help, I'm getting there slowly.

Daniel

---

### Post by oldfred on 2010-06-03
You are supposed to use gksudo with graphical applications. If it will not open gtk then try sudo, I thought nvidia settings was graphical.

sudo nvidia-settings

---

### Post by Zeophlite on 2010-06-04
**nvidia-settings** gives a "not installed" message, and **sudo apt-get install nvidia-settings** gives "E: Couldn't find package nvidia-settings"

**sudo apt-get update** gives me "W: Failed to fetch http://security.ubuntu.com/..." errors

I believe this is a network error, as when I type in 
**lshw -C network**
it comes up with my ethernet device (disabled, but with a logical name (eth0)) and my wireless device (unclaimed, with no logical name)

How do I set up my wireless from command line?



I've been searching the internet, and following some suggestions I've tried these:

putting "quiet splash nomodeset" into grub gives me the ubuntu splash image, but then goes into command line only.

**xrandr** gives me "Can't open display"

---

### Post by Zeophlite on 2010-06-05
So my current situation is that I'm stuck in command line, and I can't get updates as my wireless isn't configured.

I'm guessing if I get the desktop up then I can use the nice UI's to fix my wireless and then update my Nvidia drivers, but I'm unsure of how to boot up the desktop.

In grub I've added "nomodeset" after "quiet splash", so the Ubuntu image show's (along with 5 dots that turn red, I think), but then takes me back into a command line interface.  How do I get the desktop to boot up?

---

### Post by davidmohammed on 2010-06-06
longshot... - when you say it goes back to command line interface - on the top of the screen does it say tty7?  If not press CTRL + ALT + F7.  That should give you back your graphical interface...

---

### Post by Zeophlite on 2010-06-06
It does say tty7 at the top.
I'll try Ctrl-Alt-F7 when I get home though, thanks for the suggestion.

---

### Post by davidmohammed on 2010-06-06
if it says tty7 then the keystroke wont make any difference.

Can I suggest to get you back to a working desktop, boot with both options nomodeset and xforcevesa

i.e. your grub should look like

nomodeset xforcevesa quiet splash

---

### Post by Zeophlite on 2010-06-06
Sorry, its tty1 not tty7, I just got home checked.  Ctrl-Alt-F# for # 1 to 6 changes the screen to logins with tty# up the top.

Ctrl-Alt-F7 brings up a black screen with a underscore up the top left flashing, but nothing happens.

I'll try xforcevesa now

---

### Post by Zeophlite on 2010-06-06
Okay so trying with **quiet splash nomodeset xforcevesa** doesn't change anything (still tty1 command line), and **quiet splash xforcevesa** just turns off the monitor again.

---

### Post by davidmohammed on 2010-06-06
ok xforcevesa on its own + CTRL ALT F7 gives you black screen + cursor

and

nomodeset xforcevesa leaves you at tty1 - correct?

when you do CTRL + ALT + F7 after booting with both nomodeset xforcevesa (no quiet splash) what does that do?

---

### Post by davidmohammed on 2010-06-06
... in addition I note in your first post you had various acpi issues

can you boot with

nomodeset xforcevesa acpi=off

or

nomodeset xforcevesa noapic

if it leaves you at tty1 then don't forget to CTRL + ALT + F7 to se tty7

---

### Post by Zeophlite on 2010-06-06
I've tried the following combinations, which I've summarised below.
Booting with **nomodeset xforcevesa** (without quiet splash) gave a new result.  It initially displayed the tty1 command line interface, but after pressing Ctrl-Alt-F7 it gave about half a page of text (this was instantaneous, so I don't think it was computing this through, it was just displayed what it had before):

fsck from util-linux-ng 2.17.2
(bunch more similar lines)
* Checking battery state [OK]

and finally had a blinking underscore.

My summary:
boot command, initial display, display after Ctrl-Alt-F7
**nomodeset xforcevesa**, tty1, fsck
**nomodeset xforcevesa noacpi**, tty1, fsck
**nomodeset xforcevesa acpi=off**, tty1, fsck
**quiet splash nomodeset noacpi**, tty1, just cursor
**nomodeset acpi=off**, tty1, just cursor
**quiet splash xforcevesa noacpi**, screen off, no effect

I think that **quiet splash** just affects the verbosity of the boot up code, **nomodeset** allows tty1, and **nomodeset xforcevesa** gives a bit more on F7.  **acpi=off** and **noacpi** don't seem to do anything.

The output (that I've labelled fsck) is the last bit of output that I see on my screen before the tty1 login comes up.  As in, the computer prints out all of its booting code, then the fsck stuff, then clears and allows me to log in.

---

### Post by davidmohammed on 2010-06-06
ok - what error message is displayed when you login on tty1 and type startx?

---

### Post by Zeophlite on 2010-06-06
No error message :D

Booting with **quiet splash nomodeset** and typing **startx** at tty1 starts up the desktop correctly.  However, when I open Firefox, it gives a "can't find page" error.

Opening System -> Administration -> Network Tools and looking under Devices: Network Devices: I have just "Loopback Interface (lo)" and "Ethernet Interface (eth0)" - not my wireless device.  Also clicking the "Power" button up the top right doesn't open a menu - I had to Ctrl-Alt-F2, log in and "sudo shutdown -r now" (as I was before when I was stuck in tty1) to restart the machine (and get back into Windows to report).

As I said before, the wireless device exists, but isn't in the list:
> **Zeophlite said:**
> I believe this is a network error, as when I type in 
**lshw -C network**
it comes up with my ethernet device (disabled, but with a logical name (eth0)) and my wireless device (unclaimed, with no logical name)


I'm guessing what I need to do now is set up wireless (how do I do that) then update my Nvidia drivers, then do something to get it to boot into desktop straight away.

---

### Post by davidmohammed on 2010-06-06
well done - making some progress.  I guess you may be correct - if you can get your nvidia driver sorted then your desktop can start automatically.

if you go to administration - hardware drivers are there any nvidia graphics drivers for you to download (if you are lucky maybe your wireless driver as well!)?

can you dump the contents of lspci here?

Further question - do you have any internet access if you use your onboard RJ45 connection?

**below is something I've just recently added in another thread - maybe it will help (hopefully):**

the tab - tab doesnt display all the boot options possible.

Having googled around there doesn't seem to be a consensus for the graphics card you have.  Some people have had success with some of the options you've tried above.  Some haven't.

Others suggest boot with one of the following options: 
fb=false
vga=788
vga=791
vga=837

n.b. again some suggest booting with one of the above in combination with nomodeset.

Some have suggested booting into recovery mode and selecting fail-safe graphics...

---

### Post by Zeophlite on 2010-06-16
To clarify my following paragraph, I have two computers, an old one upstairs (XP with a Logix monitor) and a newer (but still old) one (XP with a Fujitsu monitor).  The newer one I have been trying to get wubi to start on.

So I had turned on my computer downstairs and it froze at one point (I think in the Ubuntu desktop).  I restarted it, but the screen wouldn't turn on (the standby light just flashed).  So I took it upstairs and swapped my monitors.  The older PC works fine with Fujitsu monitor.  I tried swapping back, but the new computer with the Fujitsu monitor can't get it to turn on.

I plugged the new computer into the Logix monitor, and an ethernet cable into the new computer, and it got into ubuntu (**quiet splash** - no nomodeset!) into tty1, where I typed **startx** and it started up the desktop (no need to Ctrl-Alt-F7).  I opened up network tools, and it had no connection on the ethernet - the old computer connects fine with the ethernet cable.

But after a few minutes, the computer froze.  I restarted it and the monitor wouldn't turn on.  So I plugged the Logix monitor into the old computer, it booted fine, then I plugged the new computer back into the Logix monitor and it booted up again.  (In contrast to the old into Fujitsu works, then new into Fujitsu not working).

So my new computer can't get my Fujitsu monitor to work at all, which is a problem as the Logix monitor is old and so isn't as bright anymore and is a strain to use - I compensate by using QuickGamma on XP to make it brighter, but I don't have such a tool on Ubuntu (that I know of).

The old computer works fine with the Fujitsu monitor (actually better as its brighter, and so I don't need to use QuickGamma anymore).  However its old and slow as hell, so its not really useful.

Also the new computer works with the Logix monitor (at really low brightness - this is with the brightness pushed to maximum) in both XP and Ubuntu.  However, I can't connect to the internet to download updates (for wireless and display drivers).

In the end, I want to be able to use the new computer with the Fujitsu monitor, with wireless and it booting straight into the desktop (no startx nonsense).



Apologies for the rant, you guys have been an amazing help.  I'm annoyed that I can't get my new computer to work with my good monitor, even in XP! (the new computer boots but the Fujitsu monitor doesn't turn on)

---

### Post by Zeophlite on 2010-06-17
By **sudo nano /etc/network/interfaces** in terminal, I added:
auto eth0
iface eth0 inet dhcp
Then ran **sudo /etc/init.d/networking restart**

I can open Firefox to access the internet now!

---

### Post by Zeophlite on 2010-06-17
System->Administration->Hardware Drivers gave an error:
Cannot connect to D-BUS
org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

However System->Administration->Update Manager opens and one of the updates is nvidia-current-modaliases so I hope that helps.  I'm updating all 188 now.

---

### Post by Zeophlite on 2010-06-17
Okay so during the update it gave some errors about dbus (whatever that is), and it brought up a dialogue asking if I wanted to skip installing GRUB.  It wouldn't accept when I told it to not skip, so I ended up having to tell it to skip - so now I'm scared about trying to restart my computer.

What's causing these dbus errors, and how do I check that grub is okay?

---

### Post by Zeophlite on 2010-06-18
So I ended up restarting and it rebooted fine.

I still need to boot with **quiet splash nomodeset** then run **startx** from tty1 after I log in.  How do I get it to start in the graphical login?

Good news that it now works on both monitors (Logix and Fujitsu)

I still can't get wireless to work, but the ethernet seems to work fine.

lspci gives:
```

**daniel@ubuntu:~$ lspci**
00:00.0 Host bridge: Silicon Integrated  Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge:  Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI  bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964  [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev  01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems  [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon  Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1  Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated  Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller:  Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus  controller 180 SATA/PATA  [SiS] (rev 01)
**00:09.0 Network controller:  Texas Instruments ACX 111 54Mbps Wireless Interface**
00:0b.0 Ethernet  controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev  10)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600  GT] (rev a2)
**daniel@ubuntu:~$ **

```
So it is there, just not being used.

---

