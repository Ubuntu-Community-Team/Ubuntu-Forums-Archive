---
title: "Re: Best approach - System [sdc1] harddrive upgrade"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by paulbuk on 2011-02-26
Hi Folks,
With hardrive pricing in the UK dropping like stones I want to take advantage of new 1Tb 7200rpm hardrive and replace my current system 80Gig (remember when that was LARGE!), I don't want to go through the whole 're-install' and merely want to copy the current system contents to the pending 1Tb purchase and swap so the 1TB becomes the /dev/sdc1.

/Home is currently on a further newer WD 500gb as /dev/sdb1 but can move that later.

Whats the quickest, easiest approach to do the above. (I have searched the forums but only get info not directly related to the above procedure).


I really LOVE my Ubuntu over M$ nowadays.
:)

Thanks in advance,

Paul B

PS - don't why my system drive is sdc1, I do have a 160gb also in my box but it shows as /dev/sda1?

---

### Post by ajgreeny on 2011-02-26
Have a look at [**clonezilla**]("http://clonezilla.org/") which will clone the disk and restore it to the new one, MBR included, so it should do the job in one go.

---

### Post by paulbuk on 2011-02-26
Thanks for that, 'Ghost' was the sort of tool what I had in mind. I'll go get it now.
Peace.

PB
(:

---

