---
title: "Boxes instead of letters onthe screen after installation of 7.04"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by daniel_bel on 2008-02-02
I upgraded from 6 to 7.04 using the following procedure

1.  my computer was plugged into the internet
2. restart the computer - with that 7.04 Ubuntu disk NOT in any disk
 drive!
3. login via administrator account
4. opened a terminal
5. typed in this command (NO linebreak): sudo 
cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
6. typed in this command: sudo gedit /etc/apt/sources.list
7. typed in the password for my account when prompted
8. TOTALLY REPLACEd everything that's in that file (once it opens) with
 the 
text below 
# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
 multiverse

 
9. saved that file and close it
10. now, back in the terminal, type: sudo apt-get update
11. then type: sudo apt-get upgrade
12. then type: sudo apt-get dist-upgrade
13. restart the computer after that has completely finished 

After I restarted, I think it was still Ubuntu 6, not 7.04 and there are no letters on the screen, but boxes, and there is not internet access. 

In staged 11 and 12 I was asked 2 questions which I probably answered wrong.
Can anybody give me an advice how to resurrect the system.
I am running the computer now with UBUNTU 7.04 disk in the DVD ROM

---

