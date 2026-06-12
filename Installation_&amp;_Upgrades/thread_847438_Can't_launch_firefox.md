---
title: "Can't launch firefox"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by manoka on 2008-07-02
Hello,
After I installed the newest version of the firefox (3.0) with the Synaptic Package Manager (Ubuntu 7.10), I rebooted the computer, but when I klick on the firefox icon, I get the following message:

"Error
Could not launch application
Failed to execute child process
"firefox" (No such file or directory)"

Help would be appreciated!
manoka

---

### Post by PmDematagoda on 2008-07-02
How did you install Firefox 3 through Synaptic in Ubuntu 7.10? Was it by using a third-party repository? If so, could you post that repository here.

---

### Post by goforlinux on 2008-07-02
hmm yah maybe a currupted file when you installed it? Maybe try again?

---

### Post by robertchahine on 2008-07-02
open a terminal and type
```

firefox
```
and post the output if there's some problems or errors

---

### Post by manoka on 2008-07-02
I'm not familiar with the term "third-party repository".
Actually I first downloaded it from the official firefox web site to my desktop. As I wasn't able to install it, I also downloaded and installed "ubuntuzilla-4.5.0-0ubuntu1-i386.deb". And as I couldn't figure it out how to install the new firefox with the latter, I went to the Synaptic Package Manager, selected firefox 3.0, marked for installation and klicked apply.

---

### Post by manoka on 2008-07-02
The response for typing "firefox" in the terminal is:

The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
bash: firefox: command not found

---

### Post by robertchahine on 2008-07-02
did you try to remove it and reinstall it.
(if you want to remove it it's better to use : sudo aptitude remove firefox)

---

### Post by goforlinux on 2008-07-02
This is like the 4th thread ive come by today with firefox problems something is going on there. hmmmmm NNOOOOOOO dont let me down now firefox lol ????

---

### Post by manoka on 2008-07-02
No, I read somewhere on the way, not to remove it. 
Should I try to remove the old and/or the new version?

---

### Post by robertchahine on 2008-07-02
did you before try to download the .tar.gz package and installing it from firefox website?

(download it here:[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)
and follow these instructions: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox))

---

### Post by manoka on 2008-07-02
When I signed into my hotmail account, I got a recommendation to install the new firefox, I got the link to the download from there.
I downloaded the "firefox-3.0.tar.bz2", but when I opened it, there was no "window" to klick on to install the package.

---

### Post by manoka on 2008-07-02
Okay, I followed the advices, and I'm able now to launch a new firefox version - the house (or home) symbol is different - but when I klick on "Help" and then on "About Mozilla Firefox", it still reads: "version 2.0.0.15".

---

### Post by robertchahine on 2008-07-02
oh, are you sure that you downloaded from the right link.Anyway it's ok, try this link
[http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/)

---

### Post by manoka on 2008-07-02
As I'm living in Portugal, I have downloaded it from a Portuguese server.

---

