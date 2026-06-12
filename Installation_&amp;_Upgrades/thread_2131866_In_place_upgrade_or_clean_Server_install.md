---
title: "In place upgrade or clean Server install?"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by putz3000 on 2013-04-03
As a general rule I have always avoided actual upgrades for my desktop environment. The only OS I take that chance with is OS X and even then there are complications that can arise. I have been told Ubuntu has really improved the in place upgrade from what it used to be but to date I have not yet had a solid reason to try it.

However, I do have a server project at work. It was installed with 10.04 LTS Server but never made it out of the configuration stage and into deployment. I need the newer version of Netatalk and it looks like the best way would be to upgrade the OS to the latest LTS version. Obviously I have two options, clean install & reconfigure everything or in place upgrade while hopefully preserving current configurations. 

Points for consideration: There is no actual user data on the server yet. So if the upgrade was to go south I would be bummed, but I wouldn't have lost anything other than time. What I really don't want is complications down the road due to an in place upgrade. I had a server about a year ago crash and burn after an update. "Allegedly" it was because of an in place upgrade similar to what I am debating doing. I was told that there was or might have been some legacy sources which I am assuming was believed to cause some file corruption coming off of the upgrade. Having a working system for 6 moths - 2 years and then having it crash due to an in place upgrade would not be a good thing.

So, am I being super foolish for considering an in place upgrade over a clean install? If I took note of the current source file and then checked after the upgrade and removed any old entries if they exist would I have much to fear? Have any of you performed in place upgrades on or for production servers?

Thank you for sharing your thoughts and opinions.

---

### Post by ibjsb4 on 2013-04-03
> What I really don't want is complications down the road due to an in  place upgrade. I had a server about a year ago crash and burn after an  update. "Allegedly" it was because of an in place upgrade similar to  what I am debating doing. I was told that there was or might have been  some legacy sources which I am assuming was believed to cause some file  corruption coming off of the upgrade. Having a working system for 6  moths - 2 years and then having it crash due to an in place upgrade  would not be a good thing.

You have answered your own question :) fresh install

---

### Post by dodo3773 on 2013-04-03
Backup your configuration files etc..etc.. and do a clean install.

---

