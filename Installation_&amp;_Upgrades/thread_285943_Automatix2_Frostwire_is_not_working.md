---
title: "Automatix2: Frostwire is not working"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by LuisC-SM on 2006-10-27
I Bought a Toshiba Tecra M4 and installed Dapper, after some hours I saw that Edgy was just realesd and upgraded to edgy but Frostwire dos not work, so In one blog I found a solution from **Jorge Samapayo** and will just copy/paste what he wrotes. Works just fine so here we go:> 2 Responses to "Automatix 2 for Ubuntu 6.10 Edgy Eft"

   **[SIZE="3"][COLOR="RoyalBlue"]1. Jorge Sampayo Says:[/COLOR][/SIZE]**
      October 10th, 2006 at 10:19 am

      Changes in Test4* Disabled FrostWire since its incompatible with Edgy??!!

      But actually I have frostwire in my Edgy 6.10!

      It&#347; compatible, the only thing is that you need to modify the file "/usr/lib/frostwire/runFrost.sh" with vi (nano, gedit, etc)
      -replace the first line with "#!/bin/bash" without the ""
      save and close the file
      Then open with vi or what do you use "/usr/bin/frostwire"
      -and replace the complete file for:

      #!/bin/bash
      cd /usr/lib/frostwire
      bash runFrost.sh

      and thats all, the only problem was "bash" because frostwire was using sh…
      well this worked for me


I made some changes because the first directory was wrong and also the nano gedit editors.

Regards

Luis C. Suárez

---

### Post by viper on 2006-10-27
Thanks dude i had the same issue, fixed now\\:D/

---

### Post by mrvgarg on 2006-10-27
I had this issue which was solved by installing java first through the terminal.

---

