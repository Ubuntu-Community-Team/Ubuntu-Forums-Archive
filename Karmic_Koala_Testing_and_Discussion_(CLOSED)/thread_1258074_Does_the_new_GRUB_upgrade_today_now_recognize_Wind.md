---
title: "Does the new GRUB upgrade today now recognize Windows?"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marco123 on 2009-09-04
Anyone tried it yet?

---

### Post by taavikko on 2009-09-04
[http://ubuntuforums.org/showthread.php?t=1257332](http://ubuntuforums.org/showthread.php?t=1257332)

---

### Post by drs305 on 2009-09-04
Today's grub 2 update, from what I could see, just introduced the "saved" option - allowing the user to set "GRUB_DEFAULT=saved" in /etc/default/grub to permit the last-selected *menuentry* option to be incorporated into the grub options.

---

### Post by marco123 on 2009-09-04
Thanks.  Just wondering if they'd sorted that out yet; not important to us I know, but definitely important for the final release.

Cheers, Marco.

---

### Post by Totzo on 2009-09-04
> **drs305 said:**
> Today's grub 2 update, from what I could see, just introduced the "saved" option - allowing the user to set "GRUB_DEFAULT=saved" in /etc/default/grub to permit the last-selected *menuentry* option to be incorporated into the grub options.

Can anyone confirm that this works? No joy here- GRUB_DEFAULT=saved set in /etc/default/grub and it's still booting the 1st entry every time.

I junked os-prober (assuming that it is just for the update-grub command) and added my own custom entries with the relevant parts:

saved_entry=${chosen}
save_env saved_entry

---

### Post by drs305 on 2009-09-04
> **Totzo said:**
> Can anyone confirm that this works? No joy here- GRUB_DEFAULT=saved set in /etc/default/grub and it's still booting the 1st entry every time.

I successfully tried it out and then updated my [Grub 2]("http://ubuntuforums.org/showthread.php?t=1195275") post as well as the [wiki]("https://wiki.ubuntu.com/Grub2"). I tried it only on Ubuntu kernels and a 40_custom entry I made to a rescue CD (on my hard drive).

Did you remember to run "update-grub" after making the changes?

I'd like others' results as well.

---

### Post by VMC on 2009-09-04
> **drs305 said:**
> Today's grub 2 update, from what I could see, just introduced the "saved" option - allowing the user to set "GRUB_DEFAULT=saved" in /etc/default/grub to permit the last-selected *menuentry* option to be incorporated into the grub options.

Where did you get your info. I went [HERE]("http://www.gnu.org/software/grub/manual/grub.html#index-default-1") and only found this, (if that's what your referring to) :
```
13.1.1 default

— Command: default num
Set the default entry to the entry number num. Numbering starts from 0, and the entry number 0 is the default if the command is not used.

You can specify `saved' instead of a number. In this case, the default entry is the entry saved with the command savedefault. See savedefault, for more information.
```

---

### Post by Totzo on 2009-09-04
> **drs305 said:**
> I successfully tried it out and then updated my [Grub 2]("http://ubuntuforums.org/showthread.php?t=1195275") post as well as the [wiki]("https://wiki.ubuntu.com/Grub2"). I tried it only on Ubuntu kernels and a 40_custom entry I made to a rescue CD (on my hard drive).

Did you remember to run "update-grub" after making the changes?

I'd like others' results as well.

yes, I tried putting GRUB_DEFAULT="saved" with quotes too- just in case!!!
I'll read your post and see if I've missed something.

---

### Post by Totzo on 2009-09-04
Just noticed, there are 2 commands now- update-grub and update-grub2, are they doing the same thing? I get the same terminal output from each.

---

### Post by drs305 on 2009-09-04
> **VMC said:**
> Where did you get your info. I went [HERE]("http://www.gnu.org/software/grub/manual/grub.html#index-default-1") and only found this, (if that's what your referring to) :
[CODE]13.1.1 default


Well, perhaps I should be embarrassed at not having a source. :^o  I'm not trying to be sarcastic. Maybe I should have included that they were just my observations, not drawn from anything 'official'.

I took a look at the new 00_header file, seeing what changed in the scripts. Then I experimented with the new settings, knowing how the Grub Legacy works.

I don't have anything to back it up except what I learned on my own. Documentation seems to lag on new linux packages, which is why I wrote the "Grub 2 Basics" in the first place. 

If there is anything incorrect I will be glad to remove or modify it.

---

### Post by Totzo on 2009-09-04
I assumed you'd looked here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/216178](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/216178)

It's supposed to be fixed!

---

### Post by drs305 on 2009-09-04
> **Totzo said:**
> I assumed you'd looked here:

Oh great, *after* I've done my mea culpa. d'oh!  ](*,)

Ah, I mean, yes, of course that is where I got it. Thanks for the reference Totzo.

---

### Post by Totzo on 2009-09-04
I'm getting some odd behavior here- it works for single user mode (which it shouldn't for obvious reasons as was the default with legacy grub) but not with my custom entry. Have I got this set up wrongly?

40_custom

```
#!/bin/sh -e
echo "Adding My Custom Entries Likesay" >&2
cat << EOF
menuentry "Windows Vista" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c73e96cf907ef733
	chainloader +1
}
EOF
```

---

### Post by drs305 on 2009-09-04
Well, we have pretty much hijacked this thread. Perhaps the mods will move it.

> **Totzo said:**
> I'm getting some odd behavior here- it works for single user mode (which it shouldn't for obvious reasons as was the default with legacy grub) but not with my custom entry. Have I got this set up wrongly?

My 40_custom isn't working either as it turns out but I'm still testing it. One thing I noticed is that in the 10_linux section the following line is imported correctly into grub.cfg:
> 
saved_entry=${chosen}


However, when I update grub.cfg, the same line in my 40_custom file is imported as follows and the selection is not retained:
> 
saved_entry=


If I manually edit grub.cfg and change the line to the same as the 10_linux entries ( saved_entry=${chosen} ), the selection is retained. 

I haven't figured out yet whether this is by design or a bug. 

**Update: **I have asked the Grub 2 devs about this and will post any reply here (or wherever this portion of the thread winds up).

---

### Post by Totzo on 2009-09-04
yep same thing here- my custom entry has the ${chosen} bit and it's not injected into grub.cfg when update-grub is run, odd but fascinating!

---

### Post by bear24rw on 2009-09-04
> **Totzo said:**
> Just noticed, there are 2 commands now- update-grub and update-grub2, are they doing the same thing? I get the same terminal output from each.

I've been wondering the same thing, i've used each one successfully so who knows. Anyone know the actual answer?

---

### Post by drs305 on 2009-09-04
> **bear24rw said:**
> I've been wondering the same thing, i've used each one successfully so who knows. Anyone know the actual answer?

Yes, they do the same thing. Since I'm now gunshy, I'll support my observation, using the man pages:  ;-)
> 
update-grub2 is a stub for running **update-grub** which itself is a stub
 for running **grub-mkconfig -o /boot/grub/grub.cfg** to generate a grub2 config file.


---

### Post by VMC on 2009-09-04
> **bear24rw said:**
> I've been wondering the same thing, i've used each one successfully so who knows. Anyone know the actual answer?

$ cat /usr/sbin/update-grub
```
#!/bin/sh -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```

$ cat /usr/sbin/update-grub2
```
#!/bin/sh -e
exec update-grub "$@"
```

---

### Post by Totzo on 2009-09-05
Thanks to Colin Watson for pointing this out:

[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/216178](https://bugs.launchpad.net/ubuntu/+s...b2/+bug/216178)

My /etc/grub.d/40_custom is working now:

```
#! /bin/sh -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib
echo "Adding My Custom Entries Likesay" >&2
cat << EOF
menuentry "Windows Vista" {
EOF
  save_default_entry | sed -e "s/^/\t/"
  cat << EOF
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c73e96cf907ef733
	chainloader +1
}
```

---

### Post by drs305 on 2009-09-06
And to finish things up, here is a 40_custom file, with the "saved-entry" option enabled, for Linux entries:
> 
#!/bin/sh
prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

echo "Adding SystemRescue on Hard Drive & Custom Kernel" >&2

cat << EOF
menuentry "Jaunty 2.6.28-15-custom" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
set root=(hd0,7)
linux	/boot/vmlinuz-2.6.28-15-custom root=UUID=40c00255-28k7-544l-ae7e-9dbe4e2berd8 ro quiet splash
initrd	/boot/initrd.img-2.6.28-15-custom
}
EOF

cat<< EOF
menuentry "SystemRescue" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
set root=(hd0,6)
linux   /sysrcd/rescuecd subdir=sysrcd setkmap=us
initrd  /sysrcd/initram.igz
}
EOF


---

