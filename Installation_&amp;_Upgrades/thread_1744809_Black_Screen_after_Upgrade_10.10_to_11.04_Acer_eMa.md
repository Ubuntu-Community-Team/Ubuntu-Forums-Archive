---
title: "Black Screen after Upgrade 10.10 to 11.04 Acer eMachines"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Marric on 2011-04-30
Got a black screen after upgrade from 10.10 to 11.04.

My Computer is an Acer eMachines E527

Found a solution that suited me on:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/772785](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/772785)

I) Just started Computer normally, using new Kernel and 11.04
    then the screen became black as before.
    Waited until Harddisk (Light) wouldn't work too much and boot seemed to be over.

II) IN BLIND FLIGHT (without seeing anything, since screen is black):
    1) opened the Terminal using Ctrl+Alt+F2
    2) typed my "Username" (enter)
    3) typed my "Password" (enter)
    4) typed "sudo setpci -s 00:02.0 F4.B=30" (enter)
    5) typed my "Password" (enter)

III) Could see again, big relief !

Now it is not really satisfactory to do this over and over again each time restarting my computer.

Is there any way to use a batch or use the grub to setpci ?
I'd like to install 11.04 with an USB Stick on a similar computer - how do I setpci there?

I am a newbie to Ubuntu! Please Help.

Greetings

---

### Post by Marric on 2011-05-01
Wrote a Bash script including "sudo setpci -s 00:02.0 F4.B=30", made it executable and put it in the /etc/init.d/ directory.
This works fine, but only ONCE after a boot with older Kernel version and restart on new one.
Any solutions for this?

---

### Post by ChickenBrain on 2011-05-02
> Is there any way to use a batch or use the grub to setpci ?

I have placed the command (without sudo) into /etc/rc.local

Works as designed, but of course only after everything is done the screen turns on again. Till that I am blind for any potential errors atm.

---

### Post by Marric on 2011-05-02
Thanks,

got it all figured out now (no more black screen):

To use setpci, you need to know the right device to work with.
To list all your computers devices open a Terminal and type
> lspci[http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html](http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html)


I got this:
> 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
**00:02.0 VGA compatible controller**: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
The information I need to use in setpci -s xx:xx.x F4.B=yy:
> **00:02.0** VGA compatible controllerWhere yy is the desired brightness ranging from 00 (brightest) to FF (no brightness at all)

So in my case I use
> setpci -s 00:02.0 F4.B=201) Boot new 11.04 installation
Start computer and press shift until grub menu appears.
Then highlight actual 11.04 installation (usually the first line) and press the "c" button. 
The grub command line appears and you type 
> setpci -s xx:xx.x F4.B=yyHit Escape and you'll return to grub menu, then just hit Enter to continue the boot.

2) Reboot 11.04
Open Terminal and type
> sudo gedit /etc/rc.localThen just before "exit 0" add
> setpci -s xx:xx.x F4.B=yySave and exit.

3) Install Ubuntu 11.04 from USB or Live-CD
Install and select Language, then from menu (F6) choose "nomodeset".

---

### Post by Alvensson on 2011-05-20
Many-many thanks!

---

### Post by reauxbeauxboy on 2011-06-26
Just my .02 fwiw.  For a "Newbie" to Ubuntu, that was kick-butt.  And nice description as well.  We gotta help all these people / ourselves to write more clear instructions.  Stuff like "Well, I just whackmodded the smb pipes until i found the one that was sending but not receiving from /dev and fixed it.  works great now.  

:-)

---

### Post by foresthill on 2011-06-26
Despite very similar hardware, the blank screen fix does not work on my Gateway notebook. I am running 11.04, BTW, and have never had this problem on any other Ubuntu version.

Here is my PCI-related hardware, FWIW:

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation WiFi Link 5100
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)


The only thing that has worked on my system so far has been to add the following 2 lines to my /etc/default/grub file:

[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"[/PHP]

This allows my brightness keys to work, but I have to turn up brightness manually every time I boot into 11.04.  :(

---

### Post by temerila on 2011-09-12
> **Marric said:**
> Thanks,

got it all figured out now (no more black screen):

To use setpci, you need to know the right device to work with.
To list all your computers devices open a Terminal and type
[http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html](http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html)


I got this:
The information I need to use in setpci -s xx:xx.x F4.B=yy:
Where yy is the desired brightness ranging from 00 (brightest) to FF (no brightness at all)

So in my case I use
1) Boot new 11.04 installation
Start computer and press shift until grub menu appears.
Then highlight actual 11.04 installation (usually the first line) and press the "c" button. 
The grub command line appears and you type 
Hit Escape and you'll return to grub menu, then just hit Enter to continue the boot.

2) Reboot 11.04
Open Terminal and type
Then just before "exit 0" add
Save and exit.

3) Install Ubuntu 11.04 from USB or Live-CD
Install and select Language, then from menu (F6) choose "nomodeset".
Thanks for the solution. This worked with my emachines E727. Anyhow the screen is black after resuming from being suspended/hibernated. Any ideas for getting it fixed?

---

### Post by Lividity on 2011-11-04
I own an emachines e527. Dealing with the hibernation was a hassle. This is the only computer I've had trouble running ubuntu on. I'm surprised this isn't fixed already. 

As suggested above, I added the screen brightness command to /etc/rc.local. Adding the following command corrected the brightness setting at boot time.

```

sudo nano /etc/rc.local
```

The command is added before exit0 like so:
```
x@blacktop:/etc$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

setpci -s 00:02.0 F4.B=00

exit 0

``` 

I then noticed that when the computer hibernates the screen was staying black and not waking up again. So I did the following.

```

sudo touch /etc/pm/sleep.d/screen.brightness
sudo chmod +x /etc/pm/sleep.d/screen.brightness
sudo nano /etc/pm/sleep.d/screen.brightness

```

I then pasted the following text into the newly created file:

```

#!/bin/bash
case "$1" in
    thaw|resume)
        /usr/bin/setpci -s 00:02.0 F4.B=00>/dev/null
        ;;
    *)
        ;;
esac
exit $?

```

This script sets the monitor brightness back to 100% after waking up from hibernating.

---

### Post by tuxwarrior10k on 2012-10-18
> I then pasted the following text into the newly created file:

What file would that be?

#noobs and dies

---

### Post by hgergo on 2012-10-18
> **tuxwarrior10k said:**
> What file would that be?

#noobs and dies

I think /etc/pm/sleep.d/screen.brightness

---

