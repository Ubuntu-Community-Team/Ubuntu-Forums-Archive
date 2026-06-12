---
title: "ATI Radeon HD4200  -- green and pink"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tomy on 2010-03-07
I just upgraded my motherboard to one with a ATI Radeon HD4200 IGP. My old Karmic install works fairly well with the ATI fglrx driver. 

On a new drive I installed Lucid and was surprised that the default install came up with compiz working. There is no xorg.conf -- how do I tell what graphics driver is being used? I assume it is the open source radeon driver.

The colors are all wierd with a green background and lots of pink. I can change the background to some other color but the windows are still mostly green. It doesn't much matter what theme I choose. 

I then added xorg-edgers to my sources.list and upgraded. No difference. Still green and pink. 

But my desktop cube rotates -- what a surprise! The developers have made a lot of progress with the open source ATI drivers. 

Does anyone have the Radeon HD 4200 working on Lucid?

---

### Post by rajeev1204 on 2010-03-07
I have the ATI 4850 discreet card and its working fine.

Try checking the contacts between monitor and card,this can happen due to moisture etc on the pins.

Do you have a CRT monitor? Check the monitor.

---

### Post by Tomy on 2010-03-07
Thanks, 
I've got an LCD and it works fine when I boot to Karmic. I only have problems with my new Lucid install.

---

### Post by Tomy on 2010-03-07
> **rajeev1204 said:**
> I have the ATI 4850 discreet card and its working fine.

Try checking the contacts between monitor and card,this can happen due to moisture etc on the pins.

Do you have a CRT monitor? Check the monitor.

Turns out this is good advice. 

My new motherboard has HDMI/DVI/VGA video ports and so does my LCD. I was running with a HDMI cable and I switched it to a DVI cable and now it works. Strange.

Thanks

---

### Post by rajeev1204 on 2010-03-07
> **Tomy said:**
> Turns out this is good advice. 

My new motherboard has HDMI/DVI/VGA video ports and so does my LCD. I was running with a HDMI cable and I switched it to a DVI cable and now it works. Strange.

Thanks


Aah, i believe there are issues with HDMI with the open source driver for the R 700 series ( the 4000 series) cards, so probably will be fixed in due time.

Iam not sure though.

---

