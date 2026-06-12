---
title: "Now OS Install"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by garydem on 2012-04-29
I have been using Ubuntu for years and gone through many on-line OS upgrades.  However, this one has to be the worst upgrade I have experienced.  This upgrade was attempted on a very stable HP tower computer and all looked well during the process.  When the system restarted I only got a blank screen- sometimes, because other times it would not boot.  I am forced to do a clean install but I am worried that the ISO file is also corrupt.  I would appreciate any feedback on that file quality before I install.

Thanks

---

### Post by darkod on 2012-04-29
Black screen can usually be video driver issue. Did you try to troubleshoot it or you want to go for a clean install right away?

Did you try to boot into live mode with 12.04 cd? That would show if it works fine on your hardware or there are some issues.

You can try this: In the grub2 boot menu, highlight the ubuntu entry and press 'e' for edit. That will show the boot lines. With the arrows move the cursor to the end of the line starting with linux, and add 'nomodeset' after 'quiet splash'. Press Ctrl + X to boot. See if that helps it boot.

If you have only linux and don't get a grub2 boot menu, hold Shift during boot to show it.

---

### Post by garydem on 2012-05-01
Thanks for the feedback..I needed to reload and I installed 11.10.  If now works fine......




> **darkod said:**
> Black screen can usually be video driver issue. Did you try to troubleshoot it or you want to go for a clean install right away?

Did you try to boot into live mode with 12.04 cd? That would show if it works fine on your hardware or there are some issues.

You can try this: In the grub2 boot menu, highlight the ubuntu entry and press 'e' for edit. That will show the boot lines. With the arrows move the cursor to the end of the line starting with linux, and add 'nomodeset' after 'quiet splash'. Press Ctrl + X to boot. See if that helps it boot.

If you have only linux and don't get a grub2 boot menu, hold Shift during boot to show it.

---

