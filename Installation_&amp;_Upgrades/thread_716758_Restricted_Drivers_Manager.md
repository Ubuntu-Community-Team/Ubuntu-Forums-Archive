---
title: "Restricted Drivers Manager"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by lfutc001 on 2008-03-06
OK I know this has probably been seen 1000 times, but when I try to run the Restricted Drivers Manager i get an error stating that 

You need to install the package

  linux-restricted-modules-2.6.22-14-server

for this program to work.

I was able to use Envy to get my NVidia drivers to work, but the wireless in my laptop (Intel 3945ABG) no longer does.  This happened after my upgrade from Feisty to Gutsy.

If anyone knows what I can to to get past this it would surely be helpful.

Thanks

---

### Post by wpshooter on 2008-03-06
Have you tried doing a search in Synaptic for that package ?

---

### Post by lfutc001 on 2008-03-06
I have but haven't been able to find it.  When i try apt-get it says that package doesn't exist.

---

### Post by wpshooter on 2008-03-06
Are you sure that you have all of the proper settings marked in "Software Sources" ?

Try going into Synaptic and hit the, I think it is "Reload" button.

---

### Post by lfutc001 on 2008-03-06
In software sources I have everything turned on except source code.  I hit reload and then searched for the word restricted - but that package still does not come up on the list.

---

### Post by oldos2er on 2008-03-06
If I'm not mistaken you need to enable the source code repos to get the Nvidia driver working.

---

### Post by lfutc001 on 2008-03-06
Don't know if it matters but the nVidia driver isn't my problem as far as I know.  I was able to use Envy to install those.  It's the Intel driver that I can't get to without the restricted drivers manager.

If there's another way to install the Intel wireless driver that would be ok.

---

