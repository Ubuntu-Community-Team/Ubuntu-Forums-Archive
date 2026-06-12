---
title: "Gimp upgrade problem"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by grgill on 2006-02-24
I have done the unthinkable and upgraded Gimp to 2.2.10 found in Dapper (was having printer problem and hoped upgrade would resolve it... don't know). I can't open jpeg files and get a message "unknown file type". Is this just a bug in the new package (in which case I should wait patiently for the fix) or have I done something wrong?
Greg

---

### Post by Xian on 2006-02-24
I can open jpeg files correctly using gimp 2.2.10 in a full Dapper envrionment, so I would say the package is fine. However, it may require some other iib that is not in your Breezy installation.

---

### Post by grgill on 2006-02-24
thankyou for your help. i found the problem to be that i had deleted the path to the plugins in gimp. went to "file", "preferances", "folders", "plugins" and added "/usr/lib/gimp/2.0/plug-ins" to the list. jpegs (and a lot of other things i'm sure) are back. thanks again.

---

