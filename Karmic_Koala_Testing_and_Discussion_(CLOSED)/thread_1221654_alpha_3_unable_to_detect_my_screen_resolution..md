---
title: "alpha 3 unable to detect my screen resolution."
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frustphil on 2009-07-24
Everything has gone from worse to worst. Before only kubuntu can't detect my screen resolution(even the final release of jaunty and todays karmic alphas). Now ubuntu has jumped into pack. I hope it won't be like this until the final karmic...

---

### Post by entangled on 2009-08-08
Maybe no-one else has this problem of bad screen resolution but I'll post a solution here just in case.
I'm running karmic on a Intel Mac Mini, using Intel 945GMA and monitor 1280x1024. When I boot karmic from given Grub2 menu I get max resolution of 800x600. I used to get 1280x1024 from Jaunty.
After some reading I tried putting in a kernel boot option to turn off modesetting and it worked.
I wasn't sure how to provide generic kernel boot options when using Grub2 (anyone know this?) so I made a new custom config file.
**/etc/grub.d/08_customboot**
and put in the lines
```
# This file is an example on how to add custom entries
cat << EOF
menuentry "Ubuntu, Linux 2.6.31-5-generic fullres" {
        set root=(hd0,3)
        search --no-floppy --fs-uuid --set 72b2f505-274d-44c9-8d28-a993697d9943
        linux   /boot/vmlinuz-2.6.31-5-generic root=UUID=72b2f505-274d-44c9-8d28-a993697d9943 ro   quiet splash **i915.modeset=0**
        initrd  /boot/initrd.img-2.6.31-5-generic
}

```
Note the added kernel option      i915.modeset=0.
(Of course the UUID values will be specific to your system and can be copied from the existing grub.cfg file.)
Make this file executable
**sudo chmod a+x 08_customboot**
and run
**sudo grub-install /dev/sda**
or whatever your disk device is called.
This should generate a new /boot/grub/grub.cfg file containing your entries (check it) and future boots will offer this option. 
If you don't get the new entry in the grub.cfg file (I didn't) then you have to run an explicit
**sudo grub-mkconfig -o /boot/grub/grub.cfg**
to get the config file to update (I think there is a bug in grub-install here).
Hope you can get full resolution after this.

---

### Post by taavikko on 2009-08-08
@ entangled, make your customization to default kernel boot stanza, edit "/etc/default/grub"
there's a line
" GRUB_CMDLINE_LINUX_DEFAULT="quiet splash <add your options here>" "
and update-grub

---

### Post by entangled on 2009-08-14
Thanks Taavikko, you put me right about boot options and using update-grub. I found that i915.modeset=0 works but it gives a 'not recognized' message during boot. Other options I tried, like 'modeset=0' or 'i915 modeset=0', get no boot messages but they don't work either.

---

### Post by taavikko on 2009-08-14
> **entangled said:**
> Thanks Taavikko, you put me right about boot options and using update-grub. I found that i915.modeset=0 works but it gives a 'not recognized' message during boot. Other options I tried, like 'modeset=0' or 'i915 modeset=0', get no boot messages but they don't work either.

The "not recognized" message doesn't affect in any way, just a glitch.
use "nomodeset" to disable the kms

---

### Post by frustphil on 2009-08-17
Alpha 4 has fixed this issue. Don't know about Kubuntu though..

---

