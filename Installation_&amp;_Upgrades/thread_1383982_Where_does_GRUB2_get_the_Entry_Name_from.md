---
title: "Where does GRUB2 get the Entry Name from?"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by agaul on 2010-01-17
Here is my current setup.  I have installed Windows 7 Home Premium 64-bit, Ubuntu 9.10 64-bit, and BackTrack 4 Final in that order.  All operating systems are able to boot and all is working well.  The only problem I'm faced with is really just an annoyance.  Which is BackTrack is showing up with a "Ubuntu 8.10" entry name.

Now I did some research on this.  I found out that BackTrack was based on the Ubuntu 8.10 OS so it makes sense why it would show up that way.  I found several articles and topics explaining how to modify the GRUB programming files.  I guess to change the entry name, but all of them don't seem fool proof to me nor the best way to go about doing things.

One thing I wasn't able to find info on is where GRUB2 actually gets these entry names from.  My theory is if I can find out where GRUB gets this info from, I can simply log into the BackTrack partition and change where the "Ubuntu 8.10" entry is to "BackTrack 4" and then run the update-grub2 command within Ubuntu to update the entry names.

Is such a task as simple as I make it out to be or is it technically impossible?  Please advise.  Thank you.

---

### Post by drs305 on 2010-01-17
I think I tried tracking this down once and never really pursued it. But backing up one step, Backtrack is most likely getting the name from the /etc/grub.d/30_os-prober file and the "linux" section variables. 

You can check by inspecting /boot/grub/grub.cfg and seeing which section the Backtrack menuentry is in. Each section is created by a different script and is annotated in that file.

I wrote a guide on how to change entries in the Grub 2 menu displays. It is admittedly pretty crude and I'm sure there will be better ways to handle it as we learn more about the G2 features. But if you are really into geek stuff you can refer to the "G2-Tweaks" link in my signature line to see how to alter the variables to produce a desired menu title.

The other option is to create an /etc/grub.d/06_custom file and put the entries into it exactly as you would like them to appear. It wouldn't update but is an easy way to get the titles you want. The "dynamic" menuentries would appear below unless you make the corresponding file unexecutable.

---

### Post by meierfra. on 2010-01-17
> where GRUB2 actually gets these entry names from.

/etc/lsb-release

---

### Post by agaul on 2010-01-17
> **meierfra. said:**
> /etc/lsb-release
Excellent!  But when I edit those entries to my hearts desire and do an "update-grub2" it doesn't seem to update the entry names in grub.cfg.  Although when I run the command it states that it finds "BackTrack."  Are you sure that is where GRUB2 gets those names from and if so why is GRUB2 still specifying BackTrack as "Ubuntu 8.10?"

EDIT: Just for giggles.  I went into "grub.cfg" manually and changed the entries to "BackTrack 4" then ran "update-grub2" to see what would happen.  It put "Ubuntu 8.10" back as the entry name for BackTrack even after editing the "lsb-release" file on the BackTrack partition.

EDIT2: More info on this.  It looks like the menu entry comes from the variable "LLABEL" not "LONGNAME" where it gets from the "lbs-release" file.  The programming is beyond my knowledge, but it seems as if I can find out where "LLABEL" comes from, then I should be all set.

---

### Post by meierfra. on 2010-01-17
> Are you sure that is where GRUB2 gets those names from 
No. I just looked over the os-prober script and that seemed  to be the place it got the name from. Seems I have to  have a  closer look.  Are you running "update-grub2"  in Ubuntu 9.10 or in BackTrack?

---

### Post by agaul on 2010-01-17
> **meierfra. said:**
> No. I just looked over the os-prober script and that seemed  to be the place it got the name from. Seems I have to  have a  closer look.  Are you running "update-grub2"  in Ubuntu 9.10 or in BackTrack?
I am running "update-grub2" in Ubuntu.

```
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
    save_default_entry | sed -e "s/^/\t/"
    prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
    cat <<  EOF
    linux ${LKERNEL} ${LPARAMS}
EOF
```This is where I saw that "LLABEL" was the variable for the entry name.  I guess I could always modify the script and change "LLABEL" to "LONGNAME," but I'd rather not unless it was a last resort.

---

### Post by meierfra. on 2010-01-17
Did some more testing and it seems to work like this:

If you have  a menu.lst, grub.conf or  grub.cfg on your backtrack partition, update-grub will use the entries from that file.

If not,  update-grub will generate the  entries itself and the names should come from /etc/lsb-release.

---

### Post by agaul on 2010-01-17
> **meierfra. said:**
> Did some more testing and it seems to work like this:

If you have  a menu.lst, grub.conf or  grub.cfg on your backtrack partition, update-grub will use the entries from that file.

If not,  update-grub will generate the  entries itself and the names should come from /etc/lsb-release.
That was infact the answer.  I had a "menu.lst" on the BackTrack partition and as soon as I renamed it to "menu.lst.bak" and ran "update-grub2" in Ubuntu, all is well.  My GRUB menu now has all the correct entries and all 3 operating systems are able to boot without a problem.

Your assistance is very much appreciated.  Thank you.

---

