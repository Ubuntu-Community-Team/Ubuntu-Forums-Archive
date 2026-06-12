---
title: "multiple computers upgrade"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by sagarhshah on 2006-06-10
Hi,

I have around 6 computers at home all running ubuntu breezy.
I would like to upgrade them all to dapper (no I can't do a fresh install).

Ok now here comes the question: 
Is it possible to download the upgrade packages once and then upgrade all the computers using the locally downloaded upgrade packages rather then have apt connect to the apt repositories each time for diff computers and download file again.
If you are wondering why I ask this I have a bandwidth cap on my internet connection and I can imagine an upgrade for 6 computers taking up a lot of the allowed bandwidth (and also the repositories are really slow at the moment so a fair bit of time as well).

(my linux skill level is between intermediate and advanced so I am not afraid of getting down and dirty with command line editing. infact I have broken and fixed many a system)

Any help will be appreciated
Thanks for your time

Sagar Shah

---

### Post by Dr. Nick on 2006-06-10
In that case I would download the iso image for dapper and burn it to a cd. Then open synaptic and get to the repositories section under the settings menu. From their you can add a cd-rom as a source. I think after that you should have no problems just dist-upgrading from the cd, whithout a fresh install.

I havent done this personally though

---

### Post by sagarhshah on 2006-06-10
hmm
ok I am trying that.
This is what I had to do so far

1. Download and burn Dapper alternate install cd (can only upgrade with this cd)
2. Add cd as repository by entering following command in term : sudo apt-cdrom add
3. Edit /etc/apt/sources.list so that only cdrom is not commented out. (not sure if this step is necssary)
4. invoke upgrade operation in term :sudo apt-get dist-upgrade


First computer went through upgrade operation without a hitch. Now for the other 5!!

Sagar

---

