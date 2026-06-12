---
title: "cups server error failure to connect.--can't print 15.04"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by chris15491 on 2015-05-04
any help please

i am stuck
cant print 
printer hp 1300 doesnt connect
never a problem on 14.4

---

### Post by dino99 on 2015-05-04
is it identified by the system ?
if its an usb printer, then unplug/plug it
what is shown by journalctl ?

---

### Post by chris15491 on 2015-05-04
it--my hp 1300- does not show up when i open the printer folder. any command to print -only prompts to print to file.
please tell me how to get the info you are requesting. re journalctl.

thank you for your help

---

### Post by SeijiSensei on 2015-05-04
Point a browser at [http://localhost:631](http://localhost:631).  Click on Administration in the top bar, then press the Find New Printers button.  If that doesn't work, go back then click the Add Printer button.  Enter your Ubuntu username and password when prompted.  See if you can find it that way. 

You can see whether the printer is detected by the operating system by opening a terminal and typing:
```
tail -f /var/log/syslog
```
then unplugging and replugging the USB cable.  You'll see corresponding entries appear in the log.

---

### Post by chris15491 on 2015-05-05
Firstly . thank you for helping.
I tried your 631 local host put that doesne let me choose anything . Local host box is only choiuce and it says can't conect.
when I run your teminal command here are the last several .
May  5 00:01:23 chris kernel: [ [UFW BLOCK] IN=eth0 OUT= MAC=00:27:0e:06:c4:70:f8:e4:fb:ca:c5:a8:08:00 SRC=216.58.219.194 DST=192.168.1.2 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=4834 PROTO=TCP SPT=443 DPT=41765 WINDOW=0 RES=0x00 RST URGP=0 
May  5 00:01:27 chris gnome-session[1991]: Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
May  5 00:01:30 chris systemd-udevd[28683]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory

one again thank you for trying to help

---

### Post by SeijiSensei on 2015-05-05
Are you sure CUPS is running?  Try running "sudo service cups restart" from the command prompt and see what happens.

Personally I'd use 14.04.  15.04 only has a nine-month life span; 14.04 is [supported until 2019]("https://wiki.ubuntu.com/Releases").

---

### Post by Morbius1 on 2015-05-05
After you determine if the cups service itself is running or not you might want to check the cups configuration file itself.

Run this to view it's contents:
```
sudo cat /etc/cups/cupsd.conf
```
There&#8217;s a section up front that should look like this :
> # Only listen for connections from the local machine.
    Listen localhost:631
    Listen /var/run/cups/cups.sock

Or like this if you are accessing network printers:
> # Allow remote access
    Port 631
    Listen /var/run/cups/cups.sock

If either one of these is missing you will get a connection error if you try to access localhost:631

---

### Post by chris15491 on 2015-05-05
Gentleman:
I ran both commands --------the restart resulted in nothing

the second gave a long list but not the listen for connections etc
SO
do i just find 14.04 and install
do i have to remove the 15.04?

thank you for your assistance

---

### Post by SeijiSensei on 2015-05-05
Depends on whether you have customized the system with additional packages.  You might also want to keep a copy of /home to preserve your personal files and settings.  If you're starting from scratch with 14.04 and are comfortable with disk partioning, I'd use the "something else" option during installation to create a separate partition for /home.  Then you can change the OS image without losing your personal files.

After you've saved a copy of /home, you can just install 14.04 into the same location where 15.04 resides now.

---

### Post by chris15491 on 2015-05-05
I don't have a partition. I celebrated being microsoft free with several liquid refreshments.I just posted a request for assiance in removing 15.04 and reinstalling 14.4

---

