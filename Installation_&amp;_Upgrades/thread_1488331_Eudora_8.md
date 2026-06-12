---
title: "Eudora 8"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Pan Sloboda on 2010-05-19
Trying to get Eudora 8 installed in 10.04, but when I follow the Eudora instructions it fails.  Here they are:

The README file instructs thusly: 

1.  After downloading the file, open up a terminal window. 

2.  In the terminal window type in the following: 

    sudo tar -C /opt -xvf <place where you downloaded the file> [B](I assume they mean /home/pan/Downloads/.  When I tried this, I put in sudo tar -C opt -xvf /home/pan/Eudora-8.0b9.en-US.linux-i686.tar.bz2.  Fail.  
tar: Record size = 8 blocks
tar: opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now[/B])

3.  Then create a link for easy execution by typing: 

    sudo ln -s /opt/eudora/eudora /usr/local/bin/eudora 

4.  After installation is complete, we recommend that you read the 
    README.txt file (this file) in /opt/eudora. 

5.  You will then be able to run Eudora from any command prompt 
    by just typing in "eudora" (no quotes). 

If I can get past part 2 i am sure I am ok.  Ideas what I am doing wrong?

Thank you,
Chris

---

### Post by dE_logics on 2010-05-19
> tar -C opt -xvf /home/pan/Eudora-8.0b9.en-US.linux-i686.tar.bz2

You forgot the / before opt.

---

