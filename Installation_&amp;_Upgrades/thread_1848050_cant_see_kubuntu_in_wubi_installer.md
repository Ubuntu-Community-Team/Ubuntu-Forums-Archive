---
title: "cant see kubuntu in wubi installer"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by einsteinisgaurav on 2011-09-21
I downloaded wubi more than 10 times from ubuntu and kubuntu website......when i fire up wubi....it asks me few options like C: and language and space...but it doesnt show me options in desktop environment....it shows only ubuntu....i tried samething on my friends laptop and it did show him other options like kubuntu, ubuntu netbook etc.....i dont understand why it doesnt shows me kubuntu.....i want to install kubuntu using wubi....this is so frustrating....

---

### Post by bcbc on 2011-09-21
Wubi will look for an existing Ubuntu CD image (.iso) - it's not all that smart as it looks on the root of any 'drive'. If it finds one it will limit the choice to the type that the image represents.

So, if you have a CD/USB containing Ubuntu remove it before running wubi. Or if you don't believe you have any image, check the logfile in the **%temp%** directory, e.g. for 11.04 it's %temp%\wubi-11.04-rev211.log ad it should tell you where it's finding it.

Or post the logfile here if not sure.

---

### Post by einsteinisgaurav on 2011-09-22
thanks......its too smart....my bad probably....now i can see it....but it wont boot :(:confused:
trying to do usb boot and install. i just dont want to mess up my brand new XPS 17.:lolflag:

---

### Post by bcbc on 2011-09-22
What happens when you try to boot?

---

