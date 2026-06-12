---
title: "No graphical X on a fresh Karmic alpha 3 on iMac"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DShad on 2009-07-27
Hi everyone.

It seems the new Karmic alpha 3 installation on my iMac 9,1 is not a success...

After a fresh installation, I can't get to the X (graphical desktop) and even worst, it seems I have no /etc/X11/xorg.conf file.

I tried both Kubuntu and Ubuntu: same result.

Could someone tell me how I can fix that?

I tried those same installation in MacOS using Virtualbox with success.

Thanks for your help.

---

### Post by wayne_cat on 2009-07-27
The new Xorg version probes the system to autoconfigure itself if there is no xorg.conf file. 

Try to generate  a xorg.conf with:

```
sudo Xorg -configure
```The result is a file "xorg.conf.new". Copy it to /etc/X11

```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```run startx .... any errors in Xorg log file?

```
/var/log/Xorg.0.log
```

---

### Post by tepsipakki on 2009-07-28
you don't need the conffile, the xserver can autoconfigure everything. File a bug and attach the resulting logfile to it, or better yet, run 'apport-collect <bug#>' to attach a lot of other possibly relevant information to it

---

### Post by DShad on 2009-07-28
I'd really like to send the logfile in order to let the developpers find and fix the problem, but since I'm in terminal mode, I don't find any way to transfert the logfile via internet (mail or else) since nothing has been configured yet.

I thought about transferring the file to my usb flash drive, but I'd have to mount it first. Could someone explain me how I can mount my usb drive from terminal so I can use this method in order to send you the logfile?

Thanks.

> **tepsipakki said:**
> you don't need the conffile, the xserver can autoconfigure everything. File a bug and attach the resulting logfile to it, or better yet, run 'apport-collect <bug#>' to attach a lot of other possibly relevant information to it

---

### Post by wayne_cat on 2009-07-28
> **DShad said:**
> I'd really like to send the logfile in order to let the developpers find and fix the problem, but since I'm in terminal mode, I don't find any way to transfert the logfile via internet (mail or else) since nothing has been configured yet.

I thought about transferring the file to my usb flash drive, but I'd have to mount it first. Could someone explain me how I can mount my usb drive from terminal so I can use this method in order to send you the logfile?

Thanks.

run

```
sudo tail -f /var/log/messages
```plug in the USB flash drive ... one of the lines from the tail command should tell you 
what to mount

here is an example

```
ul 28 23:06:37 macbook kernel: [ 9302.776173] usb 1-3: new high speed USB device using ehci_hcd and address 10
Jul 28 23:06:37 macbook kernel: [ 9302.909251] usb 1-3: configuration #1 chosen from 1 choice
Jul 28 23:06:37 macbook kernel: [ 9302.910426] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 28 23:06:42 macbook kernel: [ 9307.912923] scsi 5:0:0:0: Direct-Access     LEXAR    GEYSER JUMPDRIVE 1.00 PQ: 0 ANSI: 1 CCS
Jul 28 23:06:42 macbook kernel: [ 9307.915865] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jul 28 23:06:42 macbook kernel: [ 9307.917739] sd 5:0:0:0: [sdb] 1001952 512-byte logical blocks: (512 MB/489 MiB)
Jul 28 23:06:42 macbook kernel: [ 9307.929212] sd 5:0:0:0: [sdb] Write Protect is off
Jul 28 23:06:42 macbook kernel: [ 9307.933713]  sdb: sdb1
Jul 28 23:06:42 macbook kernel: [ 9307.954243] sd 5:0:0:0: [sdb] Attached SCSI removable disk


```the interesting line :

```
 Jul 28 23:06:42 macbook kernel: [ 9307.933713]  sdb: sdb1
```so I have to mount sdb1 

```
sudo mount /dev/sdb1 /mnt
```now the USB device is mounted to /mnt

---

### Post by psyke83 on 2009-07-28
> **tepsipakki said:**
> you don't need the conffile, the xserver can autoconfigure everything. File a bug and attach the resulting logfile to it, or better yet, run 'apport-collect <bug#>' to attach a lot of other possibly relevant information to it

Please, I know that auto-configuring is almost perfect, but there are instances in which we must test driver options to debug issues. Not giving users an avenue to generate a "bare" xorg.conf when needed (to test driver options) is frustrating.

---

### Post by kingborel on 2009-07-28
> **psyke83 said:**
> Please, I know that auto-configuring is almost perfect, but there are instances in which we must test driver options to debug issues. Not giving users an avenue to generate a "bare" xorg.conf when needed (to test driver options) is frustrating.

AFAIK you can, just dpkg-reconfigure xserver-xorg

---

### Post by psyke83 on 2009-07-28
> **kingborel said:**
> AFAIK you can, just dpkg-reconfigure xserver-xorg

That no longer works in Karmic, nor does "sudo Xorg -configure".

---

### Post by wayne_cat on 2009-07-28
> **psyke83 said:**
> That no longer works in Karmic, nor does "sudo Xorg -configure".

Xorg -configure still works on my Apple Macbook Pro .... Karmic with the latest updates

---

### Post by psyke83 on 2009-07-28
> **wayne_cat said:**
> Xorg -configure still works on my Apple Macbook Pro .... Karmic with the latest updates

That only works if an Xorg server isn't currently running?

---

### Post by wayne_cat on 2009-07-28
> **psyke83 said:**
> That only works if an Xorg server isn't currently running?

right ... a running Xorg blocks the command.

---

### Post by nanog on 2009-07-28
> right ... a running Xorg blocks the command. 

I wonder what the reasoning behind that was...

---

### Post by psyke83 on 2009-07-28
> **nanog said:**
> I wonder what the reasoning behind that was...

The purpose of the Xorg executable is not to generate configuration files - the "dpkg-reconfigure xserver-xorg" script was more suited to this purpose, but for some reason it is no longer functioning. I hope that it's a temporary situation.

---

### Post by tepsipakki on 2009-07-29
you can still run dexconf, which the xserver-xorg postinst used to run

---

### Post by tepsipakki on 2009-07-29
> **DShad said:**
> I'd really like to send the logfile in order to let the developpers find and fix the problem, but since I'm in terminal mode, I don't find any way to transfert the logfile via internet (mail or else) since nothing has been configured yet.

I thought about transferring the file to my usb flash drive, but I'd have to mount it first. Could someone explain me how I can mount my usb drive from terminal so I can use this method in order to send you the logfile?

Thanks.

You said that the alternate installer worked, so use the terminal and apport-collect to send the files. Configure the network first with 'dhclient eth0' or similar. Also file the bug first from another computer, or use lynx/links to do that.

---

### Post by tepsipakki on 2009-07-29
Btw, the new iMac seems to have a rather fresh nvidia chip on it, so maybe try the livecd from tomorrow. It should have a new version of the free -nv driver which supports many more cards than the old one.

---

### Post by DShad on 2009-07-31
> **tepsipakki said:**
> Btw, the new iMac seems to have a rather fresh nvidia chip on it, so maybe try the livecd from tomorrow. It should have a new version of the free -nv driver which supports many more cards than the old one.

I'm downloading the current "livecd" right now.

Will give you feedback in about an hour.  If it still doesn't work, I'll file in a bug report.

Thanks

---

### Post by DShad on 2009-07-31
Ok so here's the logfile I managed to collect.

I'm also attaching the xorg.conf I got after doing the -configure command.

Thanks for any help!

---

### Post by wayne_cat on 2009-07-31
> **DShad said:**
> Ok so here's the logfile I managed to collect.

I'm also attaching the xorg.conf I got after doing the -configure command.

Thanks for any help!

Xorg does not recognize you your card. I'm just curious ...  Can you post the result from:

```
lspci |grep VGA
```You should file a bug report now

---

### Post by jerrylamos on 2009-08-01
My dodge is to copy in /etc/X11/xorg.conf from an Alpha2 or other running image.  The various tools to create xorg.conf seem to be broken on my systems.  

Yes, I dual or triple or quad boot because the demon "update" does like to blow me up from time to time....if autoconfigure doesn't work then the attitude seems to be tough luck.

Jerry

---

### Post by tepsipakki on 2009-08-02
if you remove the xorg.conf, it should fall back to using vesa. That logfile is more interesting, because if it fails then there is a bug, and please file it against xorg-server.

---

