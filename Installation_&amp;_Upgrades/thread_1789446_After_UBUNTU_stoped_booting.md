---
title: "After UBUNTU stoped booting"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by 9000cse on 2011-06-23
Hi all. OK, after a tip I was given to change sudo 
> 
sudo su chmod 0440 /etc/sudoers 
exit
My system said enough is enough and stopped booting, would not come up. BLACK screen.
I followed the recovery process, but still a no go.  I do think the system was unstable before the above code.
So, decided to upgrade to 11.04.  But that did not fully work either. Somethings just not working. i.e. UBUNTU Software center. That star just keeps spinning, around and around.  I left it for a time, went and had dinner. so good 30 minutes, got back, and still she is turning.
So looked here and found this.

> 
sudo apt-get update
After it does what it does, lots of lines with you know what. It ends with


> 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


So, my first problem needs to be solved before I go to the next one.

Help needed guys, Please.

---

### Post by mörgæs on 2011-06-23
Please post in your existing threads rather than opening a new one. It makes it a lot easier for people to help you, if they can see the previous advice.

---

### Post by 9000cse on 2011-06-23
OK, Thanks, will do.

---

