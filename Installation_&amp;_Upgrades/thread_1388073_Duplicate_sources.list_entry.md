---
title: "Duplicate sources.list entry"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2010-01-22
When I exit from Synaptic I get a list of duplicate sources. Is there a program that helps remove them? Often I can not spot the duplicates in the software sources window.

---

### Post by wkulecz on 2010-01-22
I'm not sure how this happens but sudo apt-get update usually fixes it.

--wally.

---

### Post by Robbyx on 2010-01-22
Yes I agree it does clear it but it seems temporary because I get the error message again at another time.

---

### Post by winchendonsprings on 2010-02-01
same problem here. here is my error

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-proposed_universe_binary-amd64_Packages)

now when I view the entries in /var/lib/apt/lists/ and compare the above errors in gedit, they do not look to be duplicates to me. 

what should I do? Is it safe to delete 1 of the suggested duplicates?

---

### Post by kansasnoob on 2010-02-01
I've been seeing that with the partner repos in both Karmic and Lucid.

Strange???????????????

---

### Post by winchendonsprings on 2010-02-02
Is there a way to fix it within the Software Sources in Synaptic?

---

