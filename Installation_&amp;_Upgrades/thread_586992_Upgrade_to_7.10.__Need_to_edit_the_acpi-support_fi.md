---
title: "Upgrade to 7.10.  Need to edit the acpi-support file first"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by keithk50 on 2007-10-22
I had Fiesty installed on my laptop but after a manafacturers BIOS upgrade it would only boot so far then hang on "Saving VESA state".   After a bit of searching I managed to edit the /etc/default/acpi-support file using nano from "SAVE_VBE_STATE=true" to "SAVE_VBE_STATE=false.   This fixed the the problem and fiesty booted as before.   Great.   I did the edit by booting via Recovery option and using the command line.   A feat in itself!  

My problem is that all live Ubuntu CD's will only boot upto "Saving VESA State" but I cannot figure out how to edit the same file without the aid of a Recovery type option!   Hope I am making sense!
The only Linux live CD that fully boots is PCLinux07.   Is there anyway of editing the acpi-support file before upgrade to Gutsy.   I prefer to do a clean install rather than dist upgrade because if an upgrade failed I would be back to square one but without a recovery option. 
Any suggestions/help would be appreciated.:)

---

### Post by keithk50 on 2007-10-23
Anyone!

---

### Post by computercolin on 2007-12-29
I would also be interested in an answer to this question. I imagine it would be possible to edit the install cd image so that the acpi-support file is already changed.
I tried to add SAVE_VBE_STATE=false as a kernel argument but it didn't work.

---

