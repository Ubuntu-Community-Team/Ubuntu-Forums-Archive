---
title: "How do I &lt;--set-selections&gt; after clean install of 10.04"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by JaJaBinks on 2010-06-27
I have been following (2008) instructions on how to do a clean install without losing settings.
I used the command
<sudo dpkg --get-selections > /home/user/package.selections>
to create a list of installed applications.

My problem is that the instructions to reinstall those packages does not work. The code given is
<sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade>

However when I try and run this code I am told that "--set-selections takes no arguments"

So I need some revised code to reset the list of applications for re-installation

Hope that makes sense, thanks.:confused:

---

### Post by JaJaBinks on 2010-06-28
Thanks to all who looked. I have found another version of the --set-selection command that has worked. for those interested the code is:
sudo dpkg --set-selection < packages.txt
where "packages.txt" is the name of the file created from code:
sudo dpkg --get-selections > /home/user/package.txt

simple when you know how !!!

---

