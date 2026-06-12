---
title: "Problem with Hibernation after upgrade"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by marsgorski on 2011-10-22
Hi everyone. Ever since I upgraded to 10.10 about a week ago, my hibernation feature is not working. The computer (Dell Inspiron 1545) seems to go into hibernation without problems, but when I want to resume a get an error message saying 

> The system snapshot could not be read.
This might be a result of booting a wrong kernel or typing in a wrong passphrase.

You can continue to boot the system and lose the saved state or reboot and try again.

[Notice that you may not mount any filesystem between now and successful resume That would badly damage affected filesystem.]

Do you want to continue boot (Y/n)?I answer yes to the question and Ubuntu boots up, without the windows I left open when I hibernated.

I saw some posts from people with similar problems ([here]("http://ubuntuforums.org/showthread.php?t=1712372"), and [here]("http://ircanswers.com/ubuntu/561269/snapshot-eventually-continue-nothing-guessing")), but the difference is that they are not able to boot into Ubuntu at all, even if they answer "yes" to continue booting, while I am able to.

One more thing that might be relevant to the problem: When I upgraded to 10.10 I did not quite let the process finish; it never got to the stage where it erases the old config files after installing the new ones (see my thread [here]("http://ubuntuforums.org/showthread.php?t=1864309")).

Does anyone know how I could fix this?? My impression is that the problem may lie in the "booting a wrong kernel" part of the error message, there may be old kernel files that did not get erased during the upgrade and that could be causing this problem?? Thanks for the help in advance.

---

### Post by marsgorski on 2011-10-24
Anyone having the same problem??

---

