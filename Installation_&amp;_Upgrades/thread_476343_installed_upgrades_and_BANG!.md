---
title: "installed upgrades and BANG!"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by mpooley on 2007-06-17
Hi all
I hadnt downloaded the new upgrades for a while so last night i downloaded the backlog of 70 ish
after which when i booted up this morning I get this error
"x session: unable to write to tmp; xsession may exit with error"

which of course it does!! and i get back to the login screen - the only way out of the loop is to boot to the command line.
I have a NVidia card and am running fiesty btw.

I am a relative newby and havnt got a clue what went wrong or WHY ?  i thought this didnt happen on Linux?


Mike

---

### Post by Handssolow on 2007-06-17
I was just passing through and noticed your posting hadn't had a reply after 4 hours.
Looks to me  like an Nvidia driver issue with the latest kernel 2.6.20-16.
If so you won't be the only one, so from the cli choose instead the nv driver and hopefully you can boot to a gui screen. Look then at the Restricted Driver Manager for further information and instructions. You'll probably then have to remove your old Nvidia driver and go next to Synaptic to install the latest supported Nvidia driver. I can memember now if after a reboot Nvidia fired up or if I had first to go into the xorg configure file.

---

### Post by mpooley on 2007-06-17
Thanks!
My Nvidia seems to start ok i get the screen!  ???

---

### Post by mpooley on 2007-06-17
Hi again
I tried changinging the xorg.conf to NV instead of NVidia - the nvidia splash screen didnt come up as expected but the fault was just the same so i dont think its the drivers

please help me someone --- i 'm back using windows !!

---

### Post by mpooley on 2007-06-18
Pleeeeese! anyone out there that can help me?

Only other option i got is to re-install and if i do that i might as well stay with Windows!!!

---

### Post by luvr on 2007-06-18
> **mpooley said:**
> unable to write to tmp
I think this is the clue to what's going wrong: something is, apparently, not quite right with your **/tmp** directory. Disk full, perhaps?

---

### Post by mpooley on 2007-06-18
> **luvr said:**
> I think this is the clue to what's going wrong: something is, apparently, not quite right with your **/tmp** directory. Disk full, perhaps?

Thankyou for your reply

how would i find out and if so how  could i delete some stuff from the command line ?

Mike

---

### Post by buschi on 2007-06-18
> **mpooley said:**
> 
how would i find out


```
df -h
```

> **mpooley said:**
> 
how  could i delete some stuff from the command line ?
Mike

```
rm thefileyouwanttodelete
```

---

