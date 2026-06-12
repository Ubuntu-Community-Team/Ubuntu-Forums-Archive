---
title: "Grub2 syntax errors with 40_custom entries"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by moon_raker on 2012-11-18
Hello, 

After successfully installing a remastersys backup of Kubuntu 12.04, I disabled the os prober and added the entries I require in /etc/grub.d 40_custom as below:-
```

#!/bin/sh
echo "Adding 40_custom menu entries." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

cat << EOF
menuentry "Kubuntu 12.04 Symlink Boot" {
     linux /vmlinuz root=UUID=10b378dc-f796-429e-8d00-f54da50649d7 ro quiet splash $vt_handoff
    initrd /initrd.img
}
EOF 
 
cat << EOF
menuentry "Scientific linux 6.3" {
    set root=(hd1,5)
    chainloader +1    
}
EOF
```



Now, despite everything booting from the grub menu, everytime I run sudo update-grub there are syntax errors and a grub.cfg.new file is added.
If I remove the entries in 40_custom there are no more errors when running update-grub.
What could be the cause ? Should I ignore this as the grub menu and booting the kernels is fine ?

Edit: There are 2 Kubuntu 12.04,s now - I intend to upgrade the symlinked one to 12.10 later.

---

### Post by darkod on 2012-11-18
Is the UUID of the symlinked partition correct?

Also, you might try it with root=/dev/sdXY instead of root=UUID=....

And I would edit the 40_custom directly, not through a script, to make sure the editing is done correctly. You might have a reason to use a script.

---

### Post by moon_raker on 2012-11-24
> **darkod said:**
> Is the UUID of the symlinked partition correct?

Also, you might try it with root=/dev/sdXY instead of root=UUID=....

And I would edit the 40_custom directly, not through a script, to make sure the editing is done correctly. You might have a reason to use a script.

Solved. I simply needed to remove the cat << EOF and EOF lines. Grub 1.99> doesn't like those lines. O:)

(I also changed the +3 in the exec tail line to +4 - don't know whether that was necessary but assume it might have something to do with the Previous versions entry in grub.cfg).

---

