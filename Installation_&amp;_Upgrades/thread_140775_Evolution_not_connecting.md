---
title: "Evolution not connecting"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by VitaminG on 2006-03-06
For some reason, since I reinstalled, Evolution refuses to connect to my Gmail account. It connected without a problem in Hoary and Breezy before I reinstalled, but it now refuses to do anything other than "wait" for Gmail's reply. 
The only thing I changed between installations was to split the / partition into / and /home in preparation for the jump to Dapper. After, I reformatted and reinstalled the base system. After the install finished and I logged in, I installed a bunch of packages I had saved from the previous install by putting the packages in the /var/cache/apt directory and using Synaptic to install them offline. I then went to configuring everything else before I ran any programs. I rebooted simply to clear out the RAM, and I went to work configuring Firefox, Evolution, etc. When I tried to get my emails, though, I ran into the above problem. I've tried evreything I can think of, and still can't get it to connect or download.
Thanks in advance for any help.

---

### Post by soonindallas on 2006-03-07
sounds like a lot of changes.  did your gmail account profile get transferred ?

are you sure you're using ssl to connect to your gmail account ?

---

### Post by VitaminG on 2006-03-07
No, I didn't transfer the settings from the previous Evolution, but I have configured it several times before, so I'm quite sure it's set up as I remeber it. As far as SSL, im not sure if there's a way to specifically enable that, but I do have it set to use a secure connection for both pop.gmail.com and smtp.gmail.com always.

Edit: I got home from school and just tried Evolution without changing anything, and it is now working. Im guessing Gmail locked me out of my account for a day from when I first tried to access it with evolution, it's happened to others. Thanks again for the effort.

---

