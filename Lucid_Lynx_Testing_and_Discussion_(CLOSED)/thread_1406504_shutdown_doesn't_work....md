---
title: "shutdown doesn't work..."
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-02-14
For more than a week I have to turn-off computer via power switch. Shutdown does not work. I've tried sudo shutdown -P and all other ways but... Anyone else having the same "problem"...?

---

### Post by jppr on 2010-02-14
> **zika said:**
> For more than a week I have to turn-off computer via power switch. Shutdown does not work. I've tried sudo shutdown -P and all other ways but... Anyone else having the same "problem"...?

I don´t have any problem do normal shutdown or reboot, everything works fine

---

### Post by hikaricore on 2010-02-14
Could you be more specific about what's happening?
Nothing happens?  It hangs?  Errors?

---

### Post by jppr on 2010-02-14
> **zika said:**
> For more than a week I have to turn-off computer via power switch. Shutdown does not work. I've tried sudo shutdown -P and all other ways but... Anyone else having the same "problem"...?

Hey, i had that problem 2 or 3 days ago, i do only in terminal sudo reboot and after that system works again.

---

### Post by SecretCode on 2010-02-14
> **zika said:**
> Shutdown does not work. I've tried sudo shutdown -P and all other ways but... 

What actually happens, in detail? Are there any messages from the shutdown command?

---

### Post by dino99 on 2010-02-14
hi all,

some months ago, when karmic was a1, i had chosen to move to ext4 and grub2. Since that time i have these problems:

- if i choose " shutdown button", half time it shutdown as it has to, half time distro is closed but hardware does not stop: there is no freeze or comments in logs or else.

- if i choose "reboot button", distro is stopped but hardware not, same case as above.

So, i need unplug my system, same symptoms with jaunty, karmic or lucid as they all are drived with grub2 1.98 (lucid package).

As i understand, this problem is related to grub2. But we can wonder why some users have this problem and the others not. Is it because of hardwares or users misconfigs ? In case of users side, where to digg about wrong settings ?

Some times, i dream about a magic script able to rebuilt and overwrite wrong settings by the default distro ones. ( kind of 'dpkg-reconfigure -a boosted )

my config: asus p5whd + asus 8500 gt

---

### Post by zika on 2010-02-14
To clarify: I choose shutdown (any of several possible ways) and I get shutdown messages, disconnected from dbus, or something like that, and, then, nothing happens, it could sit like that for ages. The only way to turn off machine is to use its power switch... Reboot works OK... At the point where it stalls with shutdown I can use Ctrl-Alt-Del to reboot, also, so machine is "alive"...

---

### Post by SecretCode on 2010-02-14
Does the system boot up cleanly after this? It could be that the shutdown is fine at the OS level but the BIOS or ACPI or whatever is ignoring the final power down.

---

### Post by zika on 2010-02-14
> **SecretCode said:**
> Does the system boot up cleanly after this? It could be that the shutdown is fine at the OS level but the BIOS or ACPI or whatever is ignoring the final power down.Yes, system is booting OK. I've checked that several time, being scared that it did not unmount etc... I've reset BIOS and I've checked all the stuff in system's HW... W$ shuts down this particular machine OK...

---

### Post by SecretCode on 2010-02-14
Might be time to examine the logs then! :shock:

Open System > Administration > Log File Viewer and look in various logs for the time you last shut down. I think the relevant logs might be:
messages
syslog
pm-powersave.log
pm-suspend.log

Probably all the relevant messages will be in *messages* or *syslog* (or both). Post all the messages from the start of shutdown to the point you hit the power button, between **code** tags.

---

### Post by zika on 2010-02-14
I've checked logs...
I've waited, now, for a specific minute, just to know when attempted shutdown occured, but... there is no trace of it in messages, syslog, ... I'll keep digging but with minute hope...
It's not a big deal...

---

### Post by ronacc on 2010-02-14
this happens on my box also but I don't think it is Ubuntu as it occurs on other distros and live cd's . it started just after I replaced the power supply , I'm pretty sure in my case its a hardware problem . Does your box shutdown normally from another release or the live cd ?

---

### Post by handaxe on 2010-02-14
I can confirm the original posters symptoms - no hw changes here, started within the Lucid cycle.

I agree that the shutdown works until the point of poweroff, as "hard-off"ing does no harm and does not result in a fsck and nothing in the logs to suggest an error.

Been too lazy to search Launchpad :(  .....

HA

---

### Post by zika on 2010-02-14
> **ronacc said:**
> this happens on my box also but I don't think it is Ubuntu as it occurs on other distros and live cd's . it started just after I replaced the power supply , I'm pretty sure in my case its a hardware problem . Does your box shutdown normally from another release or the live cd ?
> **zika said:**
> W$ shuts down this  particular machine OK...
I did not try LiveCD in last several days.

---

### Post by dino99 on 2010-02-14
my errors:

dub polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale fr_FR.utf8) (disconnected from bus) (for STOP)

dub polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale fr_FR.utf8)  (for start)

(xorg.log)  (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
            (WW) Feb 14 09:41:44 NVIDIA: Failed to reserve 3072.00 MB for indirect framebuffer access:
            (WW) Feb 14 09:41:44 NVIDIA:     Cannot allocate memory

dub gdm-binary[1114]: WARNING: Unable to find users: no seat-id found

---

### Post by emarkay on 2010-02-14
Yea  me to -  just thought it's an Alpha dev bug. This happens on 2 machines.  Something about "code 15" I recall.  Will post specific "last message" nesy t time I see it. 
It seems to close all things OK, just doesn't send the "turn me off" command IMHO.  Lucid has been doing this for a while now.

---

### Post by emarkay on 2010-02-14
> **SecretCode said:**
> Might be time to examine the logs then! :shock:

Open System > Administration > Log File Viewer and look in various logs for the time you last shut down. I think the relevant logs might be:
messages
syslog
pm-powersave.log
pm-suspend.log

Probably all the relevant messages will be in *messages* or *syslog* (or both). Post all the messages from the start of shutdown to the point you hit the power button, between **code** tags.


Give me a specific files to grab  and data to post and I will get it for ya.  Yea, this may need a Launchpad check now, I see...

---

### Post by zika on 2010-02-14
Funny thing happened just now. From unknown reasons I wanted to try if plymouth works now at my machine. I installed it, reboot, and ugly "Enter" bug showed its face. I did reboot and went into "single" i.e. recovery mode. In console I purged plymouth and "reboot now" gave a cleanest shutdown I've seen in some time. Machine powered off and everything was as if I typed "shutdown -P"... Something is messed up...

---

### Post by dino99 on 2010-02-14
wich plymouth packages was installed ? plymouth-x11 ?

---

### Post by zika on 2010-02-14
No, just plymouth. Should I have installed both?
To be honest I really do not need plymouth, boot-up in the morning and boot-down at midnight and that's it...

---

### Post by dino99 on 2010-02-14
i only checked if plymouth was installed or not: only plymouth is. So i uninstall it to see if shutdown problem is related with it, but i doubt as i had this problem too with karmic without plymouth.

---

### Post by zika on 2010-02-14
> **dino99 said:**
> i only checked if plymouth was installed or not: only plymouth is. So i uninstall it to see if shutdown problem is related with it, but i doubt as i had this problem too with karmic without plymouth.No, this shutdown problem is non-related to plymouth. It just showed me that reboot can do a clean shutdown but shutdown does not make a clean reboot ... :)

---

### Post by handaxe on 2010-02-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498607]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498607")

This is the only similar bug I could find

HA

---

