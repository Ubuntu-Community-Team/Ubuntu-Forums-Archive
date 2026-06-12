---
title: "Suspend does not work"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jasonpeinko on 2008-10-13
Suspending does not work, nor does hibernation, they will suspend or hibernate to the respective states, but upon waking from them it goes to a black screen and sits there.

---

### Post by parajuito on 2008-10-13
suspend/hibernate buttons are buggy when i supend or hibernate sound went off and couldnt get it back so maybe you want to remove them xD they gave me a lot of problems

---

### Post by jasonpeinko on 2008-10-14
which buttons?

I have tried both the keyboard and the standard menu.

---

### Post by parajuito on 2008-10-14
ive just tried standard menu :S i think they are about the same :S
I found a solution for you tho xD 

(posted on [http://ubuntuforums.org/showthread.php?p=3523957#post3523957](http://ubuntuforums.org/showthread.php?p=3523957#post3523957))

install via apt-get CompizConfig
then in General Options go to Display Settings and disable Sync to VBlank


If problem persists also try changing some values in /etc/default/acpi-support

most notable change should be changing POST_VIDEO=true to POST_VIDEO=false

---

### Post by dabl on 2008-10-14
Suspend to RAM is working as expected with no issues, using kpowersave.  Kubuntu 8.10 fully updated, 4GB RAM and 2GB swap space.

---

### Post by jasonpeinko on 2008-10-14
editing the file did not work, and compiz settings manager is not in repos yet. How do i try to suspend to ram?

---

### Post by berthiggins on 2008-10-16
My suspend woes started about 2 days ago as well
at the begining of this week I could suspend and hibernate.
Now hibernate still works fine but on resuming from suspend I get the desktop wallpaper and an active cursor and nothing else.
I cannot restart X
I have no terminals
I cannot reisub to reboot only the power button works 
Any ideas?

---

### Post by jasonpeinko on 2008-10-19
You are luckier then me, i still only get a black screen.

---

