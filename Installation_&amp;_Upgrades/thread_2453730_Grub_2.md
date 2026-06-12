---
title: "Grub 2"
date: 2020-11-16
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2020-11-16
i dont know how i did it, grub aint working like it was. i have 2 drives, HDD,SSD, both are linux. {lubuntu} in one form or fashion. just, i no longer have a choice, when i boot. i should be able to fix myself. i cant. i have boot repair. but didnt want to use this as yet. i also have the grub2 disk, from a while back. GParted sees both drives, but im only going strait to /dev/sda1 on the /dev/sda drive. the other drive , /dev/nvme0n1 is not listed when i boot. /dev/nvme01p4 is not mounted, just seen that.
never mind yet. i think i found the problem. y'all are a bad influence on me. thanks

---

### Post by oneleded on 2020-11-25
i still havent found the problem. i havent asked because i thought i could figure it out with enough info online. to many answers, none specific enough.
the HDD drive is OK. the SSD drive wont or cant boot anymore. i think i have to reinstall grub2. i gotta supply more info. be back.

---

### Post by guiverc on 2020-11-25
If you can boot your system using an installed OS,  I would run 

```
update-grub
```

and watch the listing of found OSes & kernels.

I just updated another system which was three OSes
- fedora 33
- opensuse tumbleweed
- Lubuntu 20.04 LTS.

 It's Lubuntu that owns the grub, so after the fedora & opensuse had fully upgraded themselves including their own version of grub, the fedora & opensuse grub may point to the new kernels or whatever changes were made, but as those grub's aren't used by the system, the changes made will not impact the boot at all.

The final upgrade I perform is Lubuntu 20.04 LTS, as it's the one that owns the MBR on what I believe will be a MBR partitioned disk (*I forget*). Either way, I let it upgrade it's packages, then manually kick of the 

```
update-grub
```

as that's the only grub that actually runs (MBR points to Lubuntu's, not fedora or opensuse's).  It's the ownership of the MBR that matters.

---

On another box used for QA-installs, it has again many OSes
- Debian testing/sid
- Lubuntu 20.10
- Lubuntu 20.04 LTS
- Lubuntu 18.04 LTS etc...

If I do a new QA-test install to a partition (*replace partition QA-test usually*), I ensure they all boot (ie. *install didn't clobber anything & test can be reported as successful*), then boot into Debian & have it take ownership of the MBR/grub again (*it's the only OS on that box that is mine.. others are either QA-tests or used for Lubuntu support/testing*) using the

```
grub-install
```

 command.  I wonder if your issue is related to this (*other alternative is the nvme drive*)

(FYI: the other OSes allow testing of LXQt/Lubuntu issues, adding details for filing issues upstream with LXQt; opensuse tumbleweed currently the most useful; but having debian/opensuse/fedora provide alternates to the Lubuntu/LXQt which I find  useful for testing)

---

### Post by oldfred on 2020-11-26
I often run Boot-Repair just to document system. But have the old bootinfoscript which is part of Boot-Repair, but runs from terminal to document system as part of my regular backup.
While I often suggest Boot-Repair, I do not think I have ever used it to make repairs. :)

Post link to Summary Report from Boot-Repair.
Do not run any auto-fix as with multiple drives it does not always make best suggestion for fix. 
With multiple drives the advanced mode is the only one to use if using Boot-Repair to make fixes.

---

### Post by oneleded on 2020-11-27
if i unplug the first drive, HDD, and reinstall, lubuntu 20.04, on the SSD drive. 
then plug the HDD drive in, an update grub. will that fix the problem?

i lost my train of thought for the moment. Grub2 post, and saving 32 bit files, seem to be running in parallel. 
Never mind. figured that out.
Anyway, grub was working on both Linux drives till i did something. now it dont work on the SSD drive. its like it was erased, or something.
lubuntu 20.04 was acting up anyway. the desktop screen moved to the right of the screen an down. maybe i'm taking the long way around 
solving this. just do a clean install, reestablish grub that way.
the nvme drive just has the grub problem. i dont think its the SSD drive, itself.

the HHD drive has the grub problem. not the Nvme drive. just caught my mistake.
just a question;
can lubuntu update, from 18.04.4, to 18.04.5,.. .5 being 64 bits, .4 being 32 bits? Knowing this will help. and i can let ya know how that work's.

---

### Post by oneleded on 2021-01-03
its been a while, since i been here. welcome too the new year,2021. i hope to soon mark this post solved. then i'll bother ya with other questions., and i have a few. Glad ya put up with me.

---

### Post by oneleded on 2021-01-22
its a new year so to speak, i been tied up in my thoughts. let my thoughts not influence anybody. back to Ubuntu..
so, i erased the HHD. i only got one OS on the SSD.,  on P4 resides Lubuntu, 20.04... P4 is /dev/nvme0n1p4... 
i gotta show some pictures.
anyway, i want to install mint, 20.04.1..... i keep running into the problem,"no root system is defined"
i best double check this.., as i want to be accurate.

---

### Post by yancek on 2021-01-22
>   i keep running into the problem,"no root system is defined"

When using the manual install option (Something Else), you should see an Installation Type window.  Select a partition that shows in that window to which you want to install Lubuntu then click Change in the lower left of that window and select to Edit and create a Linux filesystem by formatting it as such.  You should see Mount point there so click the down arrow and select the option which shows:  /
which would be the root of the filesystem.  If you don't have a current partition available, select unallocated space and in the lower left of the window (Installation Type) click the + sign to add a partition.

---

### Post by oneleded on 2021-01-24
just wanted to add this, ^^^^   [https://www.youtube.com/watch?v=ERi0nchIw8Y](https://www.youtube.com/watch?v=ERi0nchIw8Y)
found it yesterday also.. appreciate the help. Thanks
i have lubuntu, and mint on the SSD drive now.

---

