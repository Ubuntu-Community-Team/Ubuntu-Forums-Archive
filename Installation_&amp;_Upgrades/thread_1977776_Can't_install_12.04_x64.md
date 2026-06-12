---
title: "Can't install 12.04 x64"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by DocHoliday52090 on 2012-05-10
Lenovo K230 
Desktop PC 
Core 2 Quad Q8200(2.33GHz) 
8GB DDR2 
1 TB HDD 
NVIDIA GeForce 9300 GE

I successfully installed 11.10 and ran it for a bit before a botched upgrade screwed things up. So I decided to install 12.04. 

Tried Unetbootin to do it through USB - no dice. On the UNetbootin menu when I choose an option it just hangs and flickers every now and then. 

Tried a full CD install - when I choose Install Ubuntu or Try Without Installing it goes to a black screen and blinking cursor on the top right. Doesn't go anywhere. 

I tried a minimal CD - I got through the install, but when it tried to boot after installation it progressed through the LENOVO screen but when it became time to boot up Ubuntu it shows a a couple horizontal lines of vertical lines. 

||||||||||||||||||||||||||

^ Like that, in a couple different colors. Looked like a Graphics glitch. 

My partitions are nice and setup, with a separate /home so I don't want to wipe anything :(

---

### Post by darkod on 2012-05-10
Try to boot with the cd again in Try Ubuntu. But this time as soon as the first purple screen shows up, hit Esc.
That should show the older style main menu. Hit F6 for advanced options. Select nomodeset.
Then select Try Ubuntu from the main menu.

Does that load the live mode correctly?

---

### Post by DocHoliday52090 on 2012-05-10
> **darkod said:**
> Try to boot with the cd again in Try Ubuntu. But this time as soon as the first purple screen shows up, hit Esc.
That should show the older style main menu. Hit F6 for advanced options. Select nomodeset.
Then select Try Ubuntu from the main menu.

Does that load the live mode correctly?

Yes it did. Now I see my Minimal CD install in my hard drive. Can I set nomodesetting to be the default and ressurect it?

Should I get in, update to restricted, then reinstate modesetting?

---

### Post by QIII on 2012-05-10
Dang it.  Never mind.  Too old and slow.

Staff -- Can you un-award a bean for a useless and too late post from an aging idiot?

---

### Post by DocHoliday52090 on 2012-05-10
> **QIII said:**
> Dang it.  Never mind.  Too old and slow.

Staff -- Can you un-award a bean for a useless and too late post from an aging idiot?

Not useless :) 

You can help though by teaching me how to set nomodesetting on my existing install so I can boot into it! :)

---

### Post by darkod on 2012-05-10
If you get a grub2 boot menu, highlight the ubuntu entry and hit 'e' for edit. That will show the boot lines.

Use the arrows, go to the end of the line starting with linux. Add nomodeset after 'quiet splash'.

Press Ctrl + X to boot.

Sometimes you will only need to install the nvidia driver and the problem is solved.

In other cases you will need to make the nomodeset permanent, we can discuss that later. The above method is a one time deal, it doesn't save it.

---

### Post by wojox on 2012-05-10
> **darkod said:**
> 
In other cases you will need to make the nomodeset permanent, we can discuss that later. The above method is a one time deal, it doesn't save it.

+1, when you install and reboot it will happen again. Ctrl+Alt+F1 to switch to another terminal and run:
```
sudo jockey-text -e xorg:nvidia_current
```
```
sudo reboot
```

---

### Post by darkod on 2012-05-10
> **wojox said:**
> +1, when you install and reboot it will happen again. Ctrl+Alt+F1 to switch to another terminal and run:
```
sudo jockey-text -e xorg:nvidia_current
``````
sudo reboot
```

The OP already has the OS installed, it just couldn't boot without the nomodeset. If you boot it once and the nvidia driver activation solves that, there is no need for further fixes.

---

