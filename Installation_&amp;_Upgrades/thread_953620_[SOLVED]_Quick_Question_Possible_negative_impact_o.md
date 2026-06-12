---
title: "[SOLVED] Quick Question: Possible negative impact of a &amp;quot;non-standard&amp;quot; home location?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by cjchand on 2008-10-20
Folks,

After a failed upgrade to 8.10 from 8.04, I opted to shrink the 8.04 partition and build a new partition to dedicate as the root partition. This also means that I want to keep the previous partition as my /home partition. 

I have managed to get things working by altering my two user accounts' /home directories in System -> Users and Groups. The slight side effect of this is that I have to specify the home directories as "/home/home/<userID>" since the user's folders are not in the root of the new /home partition. 

Things are working just fine, but I wanted to see if there was a major reason I should not take this approach. Is there some unforeseen consequence for having this kind of setup? 

I assume not, since you have the ability to change your /home directory, but I wanted to avoid any major caveats in the future. 

Many thanks in advance for any input!

Cheers,
CJC

---

### Post by oldos2er on 2008-10-20
In Linux, there's no such thing as a "non-standard" location for /home. As long as you have your fstab set up correctly, you should be fine.

---

### Post by 22flames on 2008-10-20
yah man honestly that sounds good you shouldent have any problems :)

22FLAMES

---

### Post by cjchand on 2008-10-20
Thanks for the replies, folks. 

@oldos2er: I think I didn't word my question properly. Let me take another shot, if I may. 

I was able to edit fstab to point to use my old partition as /home. The question was whether or not it's required that users' folders be directly under /home, as opposed to what I have currently with the path being /home/home/<userID>. 

From the sounds of things, it seems this isn't an issue, but just wanted to be sure.

Again, many thanks for the quick and knowledgeable input!

Cheers,
CJC

---

### Post by 22flames on 2008-10-20
no its not required and the guy is right there is no non standerd home .... go LINUX :)

22FLAMES

---

