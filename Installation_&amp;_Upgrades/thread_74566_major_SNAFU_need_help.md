---
title: "major SNAFU need help"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2005-10-12
hey, i started of by (trying to) boot into windows to create a stripped down version of xp to use in vmware, but i couldnt it said windows was missing the file <windows>\system32\hall.dll so i figured hell ill just reinstall it and everything will be fine, right? wrong. i remembered that if i installed xp it overwrites the MBR and erases GRUB. whenever i tried to use the recovery portion of hoary it never worked for me, so i tried expert install this time and then went to "install GRUB" it couldnt do it for some reason. so i used the recovery portion of breezy and when i typed grub-install /dev/hda it said "cant install GRUB, read only file system". so at this point i was a little fustrated and figured as a last resort ill install another copy of ubuntu then i'll be able to boot to me installation and delete this "recovery" one with no problem. i try to boot into my installation and i get this:

(normal boot up messages here)
/:clean, 27906/366528 files, 159048/732957 blocks
...done

(more messages here)

checking all files systems....
/dev/hda6 is mounted. e2fsck: cannot continue, aborting.
/home: clean, 9390/2644936 files, 818029/5293386 blocks ...fail

fsck failed. please repair manually.

so i boot into the recovery installation and run e2fsck on all three of my partitions (usr, home and /) and they all come back clean (well except for /usr which was unmounted cleanly, which ill get to why later. it ran the tests then came back clean)

i mounted the partitions to see if they were corrupt and they werent. so i tried to boot into it again. same thing.

while i was in windows, i resized the windows partition, moved the root partition over and gave the new space to /home (i did all of this with partition magic and all went well, no errors). i dont think this would have anything to do with it but ill add it in anyway, while i was in the breezy recovery mode i was mounting and unmounting partitons to see which one i needed. i believe this is why /usr was unmounted uncleanly (i belive i just hit the reset button). then all this started to happen. can someone please help me with this?

---

### Post by Brando569 on 2005-10-12
anyone have any idea on how to fix this? i really dont want to reinstall hoary, it had everything just the way i liked it :(

---

### Post by mlomker on 2005-10-12
That was somewhat confusing.  I'd recommend booting up on a Knoppix disk and confirming your partition layout:

```

fdisk -l
df -h

```

You could also try [reinstalling Grub]("http://geodsoft.com/howto/dualboot/grub.htm#install") from Knoppix.

---

### Post by Brando569 on 2005-10-13
i realized it was pointless to try and fix it, im in breezy now yay!!! :) it was definately worth downloading all of those updates (500+) :) but thanks anyway.

---

### Post by Brando569 on 2005-10-13
ok i just make another snafu, i was using adept cuz synaptic was doin it thing where it didnt wanna load sometimes. i was trying to install vmware and it was complaining that it couldnt continue cuz my kernel was compiled with gcc-3.4.2 and i was trying to use gcc-4.0.2 so i figured hey ill just downgrade gcc and everything will be fine. i forgot that adept doesnt tell you what dependencies its gonna remove, after it removed about 30 files i realized what it was removing (synaptic, open office, apt-get, etc...) so now here i am with ubuntu breezy and no way to download anything. adept is gone, synaptic is gone and apt-get is gone (among other things). would this be easy to fix or should i just reinstall breezy and download those 500+ updates again? :confused:

---

