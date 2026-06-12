---
title: "remove Lynx without killing Koala"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aceracer24 on 2010-03-09
So I asked this question in another thread under absolute beginner talk, however the answer wasn't befiting of an absolute beginner. Truth be told, I am not a complete noob, I know enough to really destroy some things.

So anyway, I installed 10.04 after 9.10 just to test and check it out. It ate it's self into a "panic" and won't boot. So I have no desire to keep the carcus and taking up valuable space. I need to know how I can remove it without borking up 9.10. Both were installed with the LiveCD and both had been installed with all default partition settings with one minor difference and that being that 10.04 was installed as a "side by side" install. 

In my previous thread I was told to boot from the liveCD and delete the 10.04 partition and allocate that empty space back to 9.10. However, thats when things get confusing. Obviously something needs to be fixed in Grub2...I don't know what or how. So could someone explain in an ABC123 kind of way?

---

### Post by ratcheer on 2010-03-09
Are Karmic and Lucid installed on separate partitions? If the answer is Yes, just boot into Karmic and run gparted. Select the partition Lucid is on and Delete it. Then Apply the change.

Then, in a Terminal window, run "sudo update-grub". You should be back in business. Reboot.

**Do not** do the above if they are not installed in separate partitions.

Tim

---

### Post by kansasnoob on 2010-03-09
Post the output of the Boot Info Script so I can be sure what's what:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by aceracer24 on 2010-03-09
Thanks guys for the info especially you ratcheer for the very simple and quick fix to my problem. However, I was impatient when I got home with no answers yet and ended up just reinstalling 9.10 from scratch. Not a huge loss but failry annoying lol. Looking forward to the stable release of lynx though.

---

### Post by slakkie on 2010-03-10
For the next time: clonezilla.org

---

