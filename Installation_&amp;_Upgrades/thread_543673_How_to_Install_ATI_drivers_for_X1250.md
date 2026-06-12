---
title: "How to Install ATI drivers for X1250"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by woody22075 on 2007-09-05
I'm new to linux and am trying to get Ubuntu running on my machine.  I have a HP 6715B with ATI X1250.  The ATI isn't supported out-of-the-box by Ubuntu.  I searched the forum and tried to use method of installing restricted drivers (as can be seen here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))

Still, no dice.  ATI offers linux drivers on their site.  I thought I would try that.  But as I am new to linux, I am not sure exactly how.  I understand that i would start this with "wget (url)" but after that, I am not sure.  

Any assistance getting Ubuntu up and running would be great!

---

### Post by dulbirakan on 2007-09-05
You do not have to go through all that.

Just click System>Administration>Restricted Drivers Manager and enable ati drivers. That is all.

---

### Post by woody22075 on 2007-09-05
Thanks for the response, dulbirakan, but I do.  I cant get Xshell running and am stuck with the command line until i get the driver up and running.  Can you answer by OP?

Thanks!

---

### Post by jocko on 2007-09-05
Try running this from a command line:
```
sudo restricted-manager --enable=fglrx
```
As far as I can understand it should work for your card.

---

### Post by mindspin311 on 2007-09-05
I should note that ubuntu lists it as a geforce2 GTS/PRO card. I thought it was a 3 or 4 series card that came with my dimension 8100, but I couild be wrong.. or the OS could be listing the wrong card.. I dunno?

---

### Post by mindspin311 on 2007-09-05
woops.. wrong thread

---

