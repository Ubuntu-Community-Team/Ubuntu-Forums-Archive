---
title: "Upgrade from 22.04 to 24.04.1 interrupted before it ends"
date: 2024-09-28
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2024-09-28
Hello,
My sister in law laptop had a power failure before the end of the upgrade. 
Upon restart, the laptop advertise itself in Noble. 
But :
1) there is still a Thunderbird deb binary in /usr/bin/thunderbird (and this is what is set to run when you select the Thunderbird icon, with data in .thunderbird and there is a Thunderbird snap installed....
2) apt autoremove found a huge amount of packets to remove.
I bet there are other problems but I did not find them yet. 
What would be the best course of action to complete the release upgrade ? 
All help will be appreciated !
Thank you for your answers.

---

### Post by oldfred on 2024-09-28
Best to make sure you have a good backup of Thunderbird & Firefox as well as rest of your data, apps & configuration.
Some are able to repair a broken update, others have to do a new install & restore from backups.

Do you want the default snap app or the .deb version?

If you want the .deb versions of Thunderbird & Firefox.
You also have to reset priorities as shown or it will reinstall the Firefox or Thunderbird snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.omgubuntu.co.uk/2024/08/install-thunderbird-deb-not-snap-in-ubuntu-24-04](https://www.omgubuntu.co.uk/2024/08/install-thunderbird-deb-not-snap-in-ubuntu-24-04)

---

### Post by georgesgiralt on 2024-09-29
Hello Oldfred
Thank you for your answer. 
I'm partial to stay with the default behaviour and settings a software has. This ensure it is as best as it will be because it is the way it has been designed and tested. Especially for my sister in law laptop as she is not a computer savvy woman.
As per the laptop itself, I think I'll reinstall it from scratch because I can't tell where the process of upgrade stopped and what steps are missing. (and even if I knew where it stopped, I'm not sure I can devise what to do to complete the process and do not miss anything behind).
So as stability and sturdiness is paramount, I'll start with a plain install and get back her files (the home directory is on a separate disk so easier to save during install)
So, I recommend that you triple check that the power supply is properly plugged BEFORE starting an upgrade ... Just my 100 000 ¢......
Have a nice and bright day !

---

### Post by georgesgiralt on 2024-10-01
Hello OldFred,
I have somewhat solved my problem. 
I did update/upgrade the packages and the snaps, cleaned the not needed anymore debs, checked the sources.list and then, worked on the Thunderbird snap not showing local folders.
For this I installed the DEB version in order to actually see what was the "normal" situation. The problem went from the fact that the local folder where quite all the emails where stored is not in the default place. The snap version whne first started copied everything except this location. So Thunderbird did not get access to it. After reverting to the Thunderbird snap version and copying the local folder content into the snap/thunderbird/common directory, everything was tip top... 
I'm not 100% sure the laptop is perfect, but.... given that I was reluctant to reinstall 24.04 this is how it goes.

Thank for your help.

---

