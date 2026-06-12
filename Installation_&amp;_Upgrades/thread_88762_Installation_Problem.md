---
title: "Installation Problem"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by LinXs on 2005-11-11
Hi Everyone
Two days ago I posted a thread but with no luck of reply, anyone care to help?

During initial installation I encounter the following error.

[COLOR="Red"][CENTER](Detecting Hardware to find CD Rom - drives)
86%
Loading Module "ide-cd" for linux ATAPI CD-ROM[/CENTER][/COLOR]

Do advice on How I might go around this issue, coz it hangs at the above.
I am running on ACER travelmate 528TE.

Thanks
Nat :???:

---

### Post by adwait on 2005-11-11
At the prompt where you press enter, try entering
```
ide=nodma
```

---

### Post by LinXs on 2005-11-11
Am I right to say at the initial before I press enter for the installation? Will try it later & let U know :) Thanks

---

### Post by LinXs on 2005-11-11
Try your instruction:

[COLOR="Red"]boot: ide=nodma
could not find kernel image : ide=dma [/COLOR]

Still couldnt do much abt it :( any advice?
Thanks
Nat

---

### Post by Huike on 2005-11-16
Try this:

boot: linux pci=noacpi (Enter)

I tried to install the 5.10 on a Travelmate 521TE and got the same errors as you. With the above boot option it worked.

---

### Post by spaschoal on 2005-11-25
Hello i am having this same error, installing on old pcchips 748/p3 700/256 ram, 3 old 10gb hds + 1 32x cdrom drive. just tried the option above, but no success.

Can anyone help please?

thanks

---

### Post by LinXs on 2005-12-13
Hi Huike,
Thanks for the help, it works now on the 528TE now. Not too sure why the problem occurs though. I am able to download most but some from the repositories. Errors still shown when installing some programs. By the way any idea on how to install jre1.5 on Ubuntu, coz on the respositories I can only add jre1.4? Thanks

---

