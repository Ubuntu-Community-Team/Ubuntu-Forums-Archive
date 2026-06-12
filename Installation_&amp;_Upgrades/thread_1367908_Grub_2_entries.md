---
title: "Grub 2 entries"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by 00b00nt00 on 2009-12-30
I would like to know how to permanently remove old kernel entries from Grub 2. I could do it under Grub, but Grub 2 seems different.

I typed: sudo apt-get autoremove

This removed the old kernels, but not the entries. What should I do next?

Please help!

---

### Post by nerdtron on 2009-12-30
I have the same problem too...how do we remove the old kernel entries in GRUB 2?

---

### Post by Azteka on 2009-12-30
In synaptic. Push "search" button - choose "provided packages" and type there linux-image-2, deselect old kernels. Don't forget about > sudo update-grub

---

### Post by Memalor on 2009-12-30
> **00b00nt00 said:**
> I would like to know how to permanently remove old kernel entries from Grub 2. I could do it under Grub, but Grub 2 seems different.

I typed: sudo apt-get autoremove

This removed the old kernels, but not the entries. What should I do next?

Please help!


1.) sudo -i
2.) cp /etc/grub.d/10_linux  /etc/grub.d/old_10_linux
3.) chmod -x /etc/grub.d/old_10_linux
4.) vi /etc/grub.d/10_linux
5.) go to the bottom of the file, there is a big 'while' loop that loads all linux images on your system.  If you are able to recover from a bad kernal manually, then you only need this to run once.  Comment out the two lines that make it loop -
#while [ "x$list" != "x" ] ; do

and at the very bottom of the file, the line that ends the loop - 

#done

If you also want to get rid of the recovery boot, comment out the 
last 'if' loop in the file also:

# if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
#    linux_entry "${OS}, Linux ${version} (recovery mode)" \
#	"single ${GRUB_CMDLINE_LINUX}"
#  fi

6.)  run update-grub

HTH

---

