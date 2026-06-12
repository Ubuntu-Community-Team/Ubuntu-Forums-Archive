---
title: "Chnaging from ATI to Nvidia"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by SlugSlug on 2012-10-22
Hi all,

Is there anything I need to remove / install when changing from ATI to nvidia card in 10.04?

---

### Post by 2F4U on 2012-10-22
Do you have proprietary graphics drivers installed? If yes, these should be remove before you switch cards.

---

### Post by SlugSlug on 2012-10-22
No its basically a fresh install

---

### Post by buckyaustin on 2012-10-22
well run this just incase, "sudo apt-get remove fglrx". Then "sudo apt-get autoremove && sudo apt-get autoclean". This should make it safe to use the other driver.

Also since this is a fresh install make sure everything is up to date. Use "sudo apt-get update && sudo apt-get upgrade". Restart then try the new card.

---

### Post by grahammechanical on 2012-10-22
Have you ran Additional Drivers and activated one of them? If so then you are using a proprietary driver appropriate for the video card that was installed at the time. You will need to de-activate it before you switch off and install the new video card.

It has been a long time since I used 10.04. I forget if it has the Additional Drivers utility. It may be that you activate the proprietary driver with the Appearance utility and select Enhanced effects.

Regards.

---

