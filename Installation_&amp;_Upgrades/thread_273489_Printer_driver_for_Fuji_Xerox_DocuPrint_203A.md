---
title: "Printer driver for Fuji Xerox DocuPrint 203A"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by iNerdSure on 2006-10-08
Anyone has the printer driver for Fuji Xerox DocuPrint 203A printer? I have googled and yahooed many places without success. Any expert in the community can help or provide a tip for an alternative? Thanks.

---

### Post by iNerdSure on 2006-10-12
Looks like I am not able to get any expert to read this posting and offer their expertise. :(

---

### Post by iNerdSure on 2006-10-27
Please, any experts or users who have some solutions, suggestions or tips to get this printer working with Dapper. Thanks.

---

### Post by rajaiskandarshah on 2006-12-06
i have the same problem here. try reading up on installing ppd files.

did try to install the ppd files, but came up with an error on something about ppd header adobe 4 ...

---

### Post by rajaiskandarshah on 2006-12-06
got it working now 

the printer is actually shared from a win xp pro machine on a network.

i am using ubuntu 6.10 on a compaq nx6120 notebook connected to the network

what i did was:

1. system > administration > printers
2. new printer
3. add a printer > network printer > windows printer (smb) > [host] > FujiXerox203A > [username] > [password] > forward button
4. manufacturer: generic > model: pcl5e printer > forward button
5. [name] > [description] > apply button

---

### Post by rajaiskandarshah on 2006-12-06
another possible work around.

try installing a similar brother or samsung driver. the printers looks very similar to each other. hopefully they share the same components.

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

you will need the cups driver as well.

the fujixerox 203a looks very similar to the brother hl-2030 printer. i have a brother hl-2040 printer at home and a brother mfc-7420 at the office which works flawlessly.

---

### Post by iNerdSure on 2006-12-12
> **rajaiskandarshah said:**
> another possible work around.

try installing a similar brother or samsung driver. the printers looks very similar to each other. hopefully they share the same components.

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

you will need the cups driver as well.

the fujixerox 203a looks very similar to the brother hl-2030 printer. i have a brother hl-2040 printer at home and a brother mfc-7420 at the office which works flawlessly.

Many thanks. Will try your suugested solution. I've almost given up hope, as there weren't any users or experts who posted any solution.

---

### Post by DonaldPK on 2006-12-16
this printer works alright with the Xerox P8e driver on Debian. for Ubuntu, try this driver.

[http://nanasbarat.dyndns.org/share/cupswrapperdocuprint_203_a-1.0.2-2.i386.deb](http://nanasbarat.dyndns.org/share/cupswrapperdocuprint_203_a-1.0.2-2.i386.deb)

---

### Post by joy_wipawee on 2006-12-20
I have the problem with that too.
Anyway, it worked after i manually add the driver of Brother HL2060 that had already existed in Ubuntu.
Easily, you plugged in USB port of your printer (FujiXerox DocuPrint 203A), then it would pop up the window of printer installation (and it showed the FX DocuPrint 203A). Then, you clicked forward and install the Brother Printer, Model "HL2060" and click Forward again. That's all.

For me, this driver, it works well with my printer.

Joy

---

### Post by iNerdSure on 2006-12-21
> **DonaldPK said:**
> this printer works alright with the Xerox P8e driver on Debian. for Ubuntu, try this driver.

[http://nanasbarat.dyndns.org/share/cupswrapperdocuprint_203_a-1.0.2-2.i386.deb](http://nanasbarat.dyndns.org/share/cupswrapperdocuprint_203_a-1.0.2-2.i386.deb)

Many thanks. Will try and see if it works on my system.

---

### Post by iNerdSure on 2006-12-21
> **joy_wipawee said:**
> I have the problem with that too.
Anyway, it worked after i manually add the driver of Brother HL2060 that had already existed in Ubuntu.
Easily, you plugged in USB port of your printer (FujiXerox DocuPrint 203A), then it would pop up the window of printer installation (and it showed the FX DocuPrint 203A). Then, you clicked forward and install the Brother Printer, Model "HL2060" and click Forward again. That's all.

For me, this driver, it works well with my printer.

Joy

Will try this as well as the solution posted by Donald. Many thanks.

---

### Post by iNerdSure on 2006-12-26
Many thanks to all who have suggested various alternative solutions. I have solved the fx 203A problem with the Samsung HL 2060 alternative. The printer works without any problems now.

Merry Christmas and best wishes for the new year 2007.

---

### Post by TonyS on 2007-10-01
Hi guys,

Mine work perfectly under 7.04 and 7.10 beta using the "Xerox DocuPrint 4508" driver.

Cheers,

Tony

---

### Post by blackmondo on 2007-10-28
> **rajaiskandarshah said:**
> another possible work around.

try installing a similar brother or samsung driver. the printers looks very similar to each other. hopefully they share the same components.

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

you will need the cups driver as well.

the fujixerox 203a looks very similar to the brother hl-2030 printer. i have a brother hl-2040 printer at home and a brother mfc-7420 at the office which works flawlessly.

Thanks a lot for sharing this tip - I just upgraded my mac to Leopard and my Xerox driver no longer worked. Used the Brother hl-2030 printer driver instead and it's all working again. 

Although I'm not running ubuntu, still much appreciated! :)

---

### Post by jeecol on 2008-06-29
Thank you everyone!

I got a printer "Fuji Xerox DocuPrint 203 A" from my brother in law. Today, I check this thread and successfully make it work on my wife's laptop (Acer Aspire 3680, Ubuntu 7.04). I selected the driver of "Brother HL 2060". 

What a coincidence! I bought Brother HL 2070N from Newegg when I was in the US. Because I heard about that this model was highly supported in Linux. However, the driver of Linux did not come with the CD (so sad), thus, I tried some existing drivers of Brother printers. Finally, I got the driver of Brother HL2060 that worked for printer HL2070N. 

Today (2008-06-29), I use the same driver again. As somebody said, Fuji Xerox DocuPrint 203A has identical looking as Brother HL 2040 (or 2030).

---------
"jeecol" means one dollar in Taiwan

---

