---
title: "Improvised &quot;dualboot&quot;?"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by Silent Warrior on 2006-08-10
I think I'm going to succumb and install Windows next to Ubuntu after all - what can I say, I like playing games. :) It's all pirates' fault, really.

Now, I have TWO harddrives, and I heard suggestions that XP would rape your MBR. Which sounds to rookies like me that I'll have to install Ubuntu again, IF I install XP on the same disc. This is where it gets interesting.
See, due in part to a somewhat uninformed purchase (or two, or more), I think I'll need to put a USB-to-IDE-adapter on that second HD. Now... What do you suppose will happen if I install XP on HD number 2 ("USB"), keeping Ubuntu as-is on HD number 1 (IDE), setting BIOS to prioritize Removable devices higher than Harddrives in the boot-order? Will it work if I disconnect the temp.-USB-HD (I'll get a SATA-one next time they fry, alright?) if I want to run Ubuntu, connect it post-boot if I desire some stuff on the other HD?
Never you mind the physical arrangement of this. I'll just... improvise, or something.

Well, do you think this will get me something like dual-boot? Or will the XP-drive go berserk? I'm not sure if the XP-installer covers this... mess, but I'm really not keen on the idea of reinstalling all this stuff AGAIN...

(If keeping both OSes on the same drive is the only way, I'll need some partition-recommendations. I've never chopped up a drive like that before...)

---

### Post by Hyter on 2006-08-10
If you install Windows after Ubuntu it will overwrite your BRUB. MBR and not reconize any linux OS. What I suggest doing is installing Windows and letting it overwrite your MBR. Then go back and reinstall GRUB. GRUB will reconize both your linux and windows os. 

Reinstalling GRUB: 
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by confused57 on 2006-08-10
I don't know anything about USB to IDE adaptors, but maybe you can glean something from this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You might have problems booting Windows if you install Windows on the same hard drive as Ubuntu if Windows is located on a partition after Ubuntu's...I've seen people actually have success with Windows on a partition after Ubuntu's partition, but not many:
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2&highlight=attempt](http://www.ubuntuforums.org/showthread.php?t=225583&page=2&highlight=attempt)

---

### Post by Silent Warrior on 2006-08-11
Heh, amazing what you can find if you take the time to look for it! :o I guess that's what I wanted to know about dual-booting. *Thinks hard* Hm... No, I don't believe I have anything to transport between the OSes that can't be taken care of with my USB-stick, if that's necessary in the first place. I'm cool, then.
Although... Computer-games tend to bloat fiercely, don't they? I happen to have a respectable number of technically open-ended-esque games - Falcon 4 (and AF), Flight Sim 2004, LOMAC, X3, NWN, to name many of 'em - that will probably be installed for a long time. Now, that other drive holds 160 Gb IIRC (Ubuntu-HD holds 80), I suspect I'd have to work really hard to fill it up, but suppose for a minute that I manage to do that. That means I would need to turn some of C: into FAT32, doesn't it? After diligent work I've almost filled 40 Gb on the Ubuntu-HD, I don't think it'll bloat much more than that, but never say never.

---

### Post by Silent Warrior on 2006-08-12
](*,) I can't be entirely sane... New development - not quite unexpected since about a month ago - means I can afford a SATA-drive now with some to spare. And SATA-connectors are all unused on my mobo. What does that tell us, everyone? It means that I can just get one o' those, copy that other HD on top of it, and install Windows on it, and nobody gets hurt. Well, not necessarily in that order. If that doesn't make things about a million times easier, I'll eat my Wing Commander-CDs...

---

