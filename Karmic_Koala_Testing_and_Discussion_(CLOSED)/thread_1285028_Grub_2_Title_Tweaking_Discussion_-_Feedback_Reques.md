---
title: "Grub 2 Title Tweaking Discussion - Feedback Requested"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by drs305 on 2009-10-07
A few days ago a person on the "ubuntu+1" IRC channel wanted to change the Windows title on his Grub 2 menu. I'm creating a short guide on how to make very minor tweaks to 10_linux and 30_os-prober to change the *titles* (and nothting more) displayed on the Grub 2 menu. For example, changing the display:
"**[COLOR="DarkRed"]Ubuntu, Linux 2.6.31-11[/COLOR]**" >>  "**[COLOR="DarkGreen"]Karmic 2.6.31-11"[/COLOR]**
or
[COLOR="DarkRed"]**"Microsoft Windows XP Home Edition on sda1"[/COLOR]** >>  "**[COLOR="DarkGreen"]XP on sda1"[/COLOR]** or "**[COLOR="DarkGreen"]XP"[/COLOR]**

My changes are fairly basic, adding a few variables, editing a few lines in the scripts, etc. Conceptually, the thread could be a place for others to post additional tweaks to the standard 10_linux and 30_os-prober.

**Feedback:**
My question for discussion: Does this go against the concept of Grub 2, whereby you can create *additional* configuration scripts such as 40_custom. Should the 10_ and 30_ files be left alone? Obviously users can do whatever they want to the files on their system, but should the approach above be encouraged?

Opinions on whether it would just be better to create a 06_custom file and have it at the top, and just allow duplication of 10_ and 30_ below; thereby not changing the system files?

**Request for solution:**
Looking for a one-line command based variable to return the codename of a specific kernel found by 30_os-prober. 

I haven't figured out how to extract the codename (karmic, hardy, etc) from installations on other partitions recognized by 30_os-prober. In 10_linux, I can get the codename using a combination of *lsb_release* and *cut*. 

I can't use the "lsb" command for other Linux installs since it only returns the *current* codename. I could create a series of if/thens based on kernel numbers, but I don't want to do that.

Comments?

---

### Post by dino99 on 2009-10-07
I think there is no interest to tweak grub.conf, except the xx_custom, because this file is only storing the result of update-grub & os-prober which give the names they want. If we previously tweak grub.conf, it is rewritten after each kernel updates or initramfs, ... with the low level naming strategy.

---

### Post by drs305 on 2009-10-07
> **dino99 said:**
> I think there is no interest to tweak grub.conf, except the xx_custom, because this file is only storing the result of update-grub & os-prober which give the names they want. If we previously tweak grub.conf, it is rewritten after each kernel updates or initramfs, ... with the low level naming strategy.

The tweaks would be to the files that **generate** grub.cfg, thus they would update the menu anytime update-grub was run. That is perhaps one of the advantages over a static 40_custom file. The scripts wouldn't have to be revised unless the file was replaced during an update.

---

### Post by dino99 on 2009-10-07
To follow your idea, default/grub seem to be the good place. 

As grub2 use uuid for identification, it should be able to recognize label or/and /dev/sdx, and follow user tweak in default/grub.

---

### Post by jmmL on 2009-10-07
> 
**Request for solution:**
Looking for a one-line command based variable to return the codename of a specific kernel found by 30_os-prober. 

I haven't figured out how to extract the codename (karmic, hardy, etc) from installations on other partitions recognized by 30_os-prober. In 10_linux, I can get the codename using a combination of *lsb_release* and *cut*. 


I recently learned about this: ```
lsb_release -cs
```Hope this is what you're looking for.

---

### Post by ranch hand on 2009-10-07
I think that the more information we have on grub2 the better, whether we use it or not.

I know that, right now, there is a thread asking how t o"center" the menu on the screen.

We are tweeking /etc/grub.d/05_debian-theme, /etc/grub.d/40_custom (or 0X_custom) and /etc/default/grub.  I seriously doubt that adding another file to this list will kill kittens.

Let the  FUN begin.

---

### Post by drs305 on 2009-10-07
> **jmmL said:**
> I recently learned about this: ```
lsb_release -cs
```Hope this is what you're looking for.

Thanks for the input. As I understand it, the lsb_release command is always going to return the *current* version. I believe it would be accurate to use its return for entries in 10_linux [COLOR="DarkRed"](correct me if not)[/COLOR]. When 30_os-prober runs, it finds other installations on other partitions. The variables currently available in the file allow for designating the linux OS is by release (8.04) and/or kernel (2.6.31...) but not by codename (hardy). 

Therefore, I couldn't present a variable such as the following because it would *always* return "karmic", or whatever I was running.
codename="`echo lsb_release -cs`"

---

### Post by emarkay on 2009-10-07
Yea it was fun to put the "$" in Windows, wasn't it.

I think there should be a way to do this.  Are those names ("Windows XP Home User" or whatever) stored in templates or ar grabbed from somewhere outside of GRUB2?

---

### Post by dinxter on 2009-10-07
you can edit/replace pretty much everything as part of a custom executable in /etc/grub.d/. update-grub works on a file called /boot/grub/grub.cfg.new while it runs. A script can edit this when update-grub is called. for example, i have an entry on a standard update-grub,
```
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
        insmod ntfs
        set root=(hd2,1)
        search --no-floppy --fs-uuid --set 96e434fbe434dee5
        drivemap -s (hd0) ${root}
        chainloader +1
}

```With an executable /etc/grub.d/50_rename
```
#!/bin/bash
sed -i 's/menuentry "Microsoft Windows XP Professional.*/menuentry "Windows XP" {/g' /boot/grub/grub.cfg.new

```This then becomes,
```
menuentry "Windows XP" {
        insmod ntfs
        set root=(hd2,1)
        search --no-floppy --fs-uuid --set 96e434fbe434dee5
        drivemap -s (hd0) ${root}
        chainloader +1
}

```In theory you can do this with any part of your grub.cfg, and it will be run as part of any automatic update-grub runs so no further fiddling is needed once its done. A rough example but you can see how much cleverer things can be done without altering any of the grub supplied standard scripts

---

### Post by cecilpierce on 2009-10-07
Thanks drs305, anything done with grub2 to make it better or easier to understand would be great in my opinion. Its been giving me a head ache since it came out.

---

### Post by drs305 on 2009-10-07
Thanks for the inputs.

I have the basic post mostly complete. I am still searching for a way to 'pull' a codename for a discovered kernel.

In 30_os-prober, I would like to be able to do something like this:
> 
linux_entry "${codename} ${kernel}" \
     "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} 
${GRUB_CMDLINE_LINUX_DEFAULT}" \
     quiet


Producing a display of:
**Karmic 2.6.31-12**
 
The kernel isn't a problem - just finding a way to pull in the "non-active" codename of the kernel into the variable a simple manner.

---

### Post by drs305 on 2009-10-08
I'm still looking for a way to extract the codename from an installed but "not-in-use" ubuntu partition. 

I've made a little progress. I can get it with the following for any **mounted** partition:
```

cat /mountpoint/etc/*eleas* | grep "CODENAME" | cut -d'=' -f2

```

When update-grub/os-prober runs, is there a way for me to read a partition and run the above command without ensuring the partition isn't mounted before running update-grub? 

If Grub 2 mounts the device to read the info, is there a way for me to find out the mount point so I can read it while os-prober is updating?

---

