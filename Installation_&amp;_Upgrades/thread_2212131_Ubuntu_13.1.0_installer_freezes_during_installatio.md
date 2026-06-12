---
title: "Ubuntu 13.1.0 installer freezes during installation"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by nate6 on 2014-03-19
Greetings all,  
I've got a Dell XPS with 2 ghz dual core processor  64 bit that I'm trying to install 13.1.0 on.
I start the install and it freezes after accepting the 3rd party software.  Any ideas?
I'm installing from a DVD which has the ISO image on it.

---

### Post by Bashing-om on 2014-03-20
nate6; Hi !

Did you verify the .iso integrity ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
Did you burn as an image s l o w l y ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Did you "check the disk for defects" from the DVD boot options screen ?

IF all the above is done, then we are looking at the requirement to set some boot options from the DVD boot options screen.

More to follow.

[INDENT][INDENT]'buntu
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 7sbaV8Kt5PTh on 2014-03-20
I had a similar issue a while ago, I had to just install the SSH server and postgres and then finished the install, then install the 3rd party stuff afterward.  It is rumored (someone told me that it took a long time to check dependencies).

---

