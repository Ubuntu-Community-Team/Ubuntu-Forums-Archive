---
title: "No graphic interface"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by RedRim on 2010-02-24
Hello friendly volunteers!

I have an HP EliteBook 8530p with windows 7 ultimate (upgraded from vista pro)

I installed Ubuntu from a liveCD with Ubuntu 9.10 on it. The live CD worked great but now I've installed it I only get a black screen with white text upon booting. I fill in my username and password and then I get some MS-DOS-like screen.

When choosing from the bootloader (GRUB) I choose:
Ubuntu, Linux, 2.6.31-19-generic-pae

I really have no idea what to do and no experience in Ubuntu.

btw, booting windows 7 does still work but I get this screen that counts down to 0, it wants to do an integrity check or something? Anyways, I let it run and then it crashes.

I'm totally puzzled and hope you guys can help me.

---

### Post by RedRim on 2010-02-24
Hey, I solved the windows thing!

This means I still got the no graphic interface Ubuntu problem.

I'll keep searching, but please give me some pointers!

---

### Post by amsterdamharu on 2010-02-24
In the grub menu there should be a recovery menu, try that one and later on you get a fix x option, choose that one. After you can choose resume normal boot.

---

### Post by RedRim on 2010-02-24
I just noticed my anti-virus (mac-afee enterprize 2010) has been disabled and I can't re-enable it. 

Did someone hack me while I was messing with sensitive files?

---

### Post by RedRim on 2010-02-24
Antivirus: solved

Solution offered: tried and failed (still no graphic interface)

Current problem: No graphic interface when launching Ubuntu

---

### Post by amsterdamharu on 2010-02-24
Ok so fix x in the recovery boot didn't work.

When you boot you get the grub menu, highlight the ubuntu normal menu and press e to edit the commands. There should be a line with
linux ....
or 
kernel ...

At the end add the following:
noacpi xforcevesa

If you can boot without problems run update manager and after all the updates check hardware drivers, both can be found under system -> administration

---

### Post by RedRim on 2010-02-24
Ok, I tried the following: 
[http://www.ubuntux.org/how-to-start-the-gui-from-the-prompt-screen](http://www.ubuntux.org/how-to-start-the-gui-from-the-prompt-screen)

And I failed

I'm really running low on sympathy for ubuntu here...

---

### Post by amsterdamharu on 2010-02-24
Try this first:
_(see reply 6)_
If that didn't work you might try to update from commandline:
```
sudo su
sudo apt-get update
sudo apt-get upgrade
```Hope that will work for you, if it fails please note the error you get and post it here.

---

### Post by RedRim on 2010-02-24
Ok I tried what you said with the following results:

1. I don't know if changing the command line in grub really did anything

2. sudo su doesn't do anything

3. sudo apt-get update gives me "unable to fetch and could not resolve"

4. sudo apt-get upgrade gives me "unable to fetch"

Man, I shouldn't be running an os that's too complicated for me to use, what problems am I going to encounter after this? I mean, it's just booting!!!

---

### Post by amsterdamharu on 2010-02-24
> Man, I shouldn't be running an os that's too complicated for me to use, what problems am I going to encounter after this? I mean, it's just booting!!!Welcome to Ubuntu. It might take some time to set it up if you're completely new to Linux and Ubuntu. Seems that you are unlucky and have some unsupported hardware (videocard). Once it is set up you should make a copy of your system, if an update screws it up or if you accidentally changed something and can't undo you can always restore the backup. I have been lucky so far on 5 computer installs.

Right now let's see how we can get it booting (with a GUI). I might not be clear in my previous post. At the end of the kernel ... or linux ... line add the following: noacpi xforcevesa single
It might look like this:
```
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=c728500b-6aed-4aa2-972f-eb6d8723c2a1 ro quiet splash **noacpi xforcevesa single**


```I added single there as well.
Not sure what the options are after editing, make sure it's saved so press e again before booting from it to make sure the changes are being used.

The dos looking thing is Linux, the desktop things are just Gnome like the old windows that ran under Dos. You have 7 of those dos prompt and can switch between them using control + alt + F1 through F7, can you check them all and see if there is any error displaying that could give us a clue what is going on?

---

### Post by RedRim on 2010-02-24
Back again

I tried the "noacpi xforcevesa single" thing and it just gave me the same blue menu as pressing recovery does.

I also tried the sudo things again and sudo apt-get update got me the following menu (in F6)

RedRim login: [      62.649286] btusb_int_complete: hci 0 urb f6087900 failed to resubmit (19)
[62.549347] btusb_bulk_complete: hci 0 urb f6087000 failed to resubmit (19)
[62.650298] btusb_bulk_complete: hci 0 urb f6087e00 failed to resubmit (19)
[62.650447] btusb_send_frame: hci 0 urb f4891180 submission failed

btw, sudo upgrade always gives me this: "blabla 5509 kb will be freed, continue? y/n
no = abort
yes = regular fail

---

### Post by amsterdamharu on 2010-02-24
Not sure what to check now, for an upgrade you need to be connected to the Internet as it will download all things that have changed since the CD came out.

Did starting the gui (graphical login) give you any error?

```
sudo /etc/init.d/gdm start
```

---

### Post by RedRim on 2010-02-24
Hey

When I enter /etc/init.d/gdm start, I get the following:

rejected sendmessage.1matched rule; type:"method_call", sender=1.102"(uid=1000 pid=2084 comm="start)interface="com.ubuntu.Upstart0_6.job"member="start"error name="(unset)"request_reply=0destination="com.ubuntu.upstart"(uid=0 pid=1 comm="/sbin/init"))

---

### Post by amsterdamharu on 2010-02-24
I don't know, think we are out of options here. So far we tried:

1.
Upgrading with apt-get update and apt-get upgrade. Failed with "unable to fetch and could not resolve" (not connected to the Internet?)

2.
Boot in recovery and choose fix x or x fix in second menu. Failed without an error.

3.
Booting with the parameters: noacpi xforcevesa **single** (added single to see if you get into recovery to see if the parameters are being used). Failed without an error.

4.
Start gdm with /etc/init.d/gdm start Failed with: rejected sendmessage.1matched rule; type:"method_call", sender=1.102"(uid=1000 pid=2084 comm="start)interface="com.ubuntu.Upstart0_6.job"m ember="start"error name="(unset)"request_reply=0destination="com.ubun tu.upstart"(uid=0 pid=1 comm="/sbin/init"))

Not sure what's going on here, can you boot with the CD and choose "try ubuntu" to see if the live cd version works?
If it does I would like the see the output of the following command:
```
lspci | grep VGA
```

---

### Post by RedRim on 2010-02-24
Yeah I just kinda destroyed my Ubuntu CD-roms (both)

I'd preferr you give me a good tutorial on uninstalling grub and ubuntu (+ repartitioning)

---

### Post by RedRim on 2010-02-24
Really, I mean it.

If you can't help me fix it, at least help me restore my previous settings, what kind of people are you?!?

---

### Post by amsterdamharu on 2010-02-24
Sorry to hear Ubuntu isn't for you.

I think you can boot from Windows CD and choose restore mbr or something to get grub out.

In Windows you can go to start -> run -> type mmc -> ok (or run) -> file -> add remove snap in -> disk manager. 
The disk manager pretty much explains itself.

If you installed wubi (windows based Ubuntu installation) than you can just remove Ubuntu with the add remove programs:
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

