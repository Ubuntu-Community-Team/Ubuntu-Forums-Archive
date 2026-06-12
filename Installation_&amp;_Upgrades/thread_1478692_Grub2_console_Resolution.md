---
title: "Grub2 console Resolution"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by mr_skater99 on 2010-05-10
Hi all,

Let me premise this with yes I have searched the forums and google but I cannot find a answer to my specific question.

Previously on my Lenovo s10-2 (1024x600 netbook) I had Ubuntu 9.10 and Backtrack 4.

Grub 2 was installed with the Ubuntu install and I upgraded the Backtrack install to use Grub2 as well for consistency.

On the Ubuntu install I added the following to the /etc/default/grub file:
  GRUB_GFXMODE=1024x600x32

And then added to the /etc/grub/00_header file (in the right spot):
  set gfxpayload=keep

And ran sudo update-grub.

I could then boot either Ubuntu 9.10 or Backtrack 4 with a console at 1024x600 with no issues.

Last week I did a fresh install of Ubuntu 10.04 and did the same as above.  Works fine for Ubuntu, but for Backtrack I just get a blank console on boot.  It does boot fine, and if I login and type startx it starts x, but if I logout it drops be back to a blank screen.

I can see that they are running different versions of grub2 - but can;t find much on why this is happening.

Any suggestions?

Cheers/

---

### Post by dino99 on 2010-05-10
> **mr_skater99 said:**
> Hi all,

Let me premise this with yes I have searched the forums and google but I cannot find a answer to my specific question.

Previously on my Lenovo s10-2 (1024x600 netbook) I had Ubuntu 9.10 and Backtrack 4.

Grub 2 was installed with the Ubuntu install and I upgraded the Backtrack install to use Grub2 as well for consistency.

On the Ubuntu install I added the following to the /etc/default/grub file:
  GRUB_GFXMODE=1024x600x32

And then added to the /etc/grub/00_header file (in the right spot):
  set gfxpayload=keep

And ran sudo update-grub.

I could then boot either Ubuntu 9.10 or Backtrack 4 with a console at 1024x600 with no issues.

Last week I did a fresh install of Ubuntu 10.04 and did the same as above.  Works fine for Ubuntu, but for Backtrack I just get a blank console on boot.  It does boot fine, and if I login and type startx it starts x, but if I logout it drops be back to a blank screen.

I can see that they are running different versions of grub2 - but can;t find much on why this is happening.

Any suggestions?

Cheers/

[COLOR="Blue"]into  /etc/default/grub

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep[/COLOR]

then : sudo grub-mkconfig && update-grub

---

### Post by mr_skater99 on 2010-05-10
Thanks for the suggestion dino99.

I had previously tried 'GRUB_GFXPAYLOAD_LINUX=keep'  I added it again to be sure and did the extra step of 'grub-mkconfig' which completed successfully (along with update-grub).

However no change in behavior.

Any other suggestions?

---

