---
title: "E: Unable to locate package update"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by b-snacks on 2010-11-04
[FONT="Trebuchet MS"]Hey Guys, I'm new to ubuntu and after alot of work with my system, I've gotten most of it working It's a Toshiba C655-S5049 with a Atheros AR9285 Wireless card, so lots of fun getting that to work, anyway I'm trying to update my system, and it wont update, if I try update manager it won't do it because it's dealing with restricted drivers, and if I try in terminal I get [/FONT] [FONT="Courier New"]E: Unable to locate package update[/FONT]Anyway, any suggestions? I've been trying to work this out, and it's getting annoying. The key Drivers that I'm also looking for are, **Video:**Intel 4500M HD Integrated with Dynamic Sharing **Audio:**IntelAudio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) Also, does anyone happen to know how well battlefield 2 will run in wine? it ran pretty good on windows, just wondering how it will do in ubuntu. Thanks a bunch!

---

### Post by P4man on 2010-11-04
run

```
sudo apt-get update
```

in a terminal and copy paste the full output. Maybe you just need to select a different mirror in your software sources.

Neither the videocard nor the audiocard require additional drivers though. AFAIk, both are supported (in the kernel and through alsa). What issues are you having with them?

---

### Post by prashant.g on 2011-12-03
Hi! i have installed ubuntu 11.04 on my desktop. i'm getting problem while installing new packages. i'm getting the same error message when i install any package. 
e.g when i'm  going to install galculator i get - E: Unable to locate package galculator 


then with above reference i tried - sudo apt-get update
then it ends after 22% installation with a big error message i'm posting last few lines here


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.177 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

please give me any suggestion to get out of this.!!!

---

### Post by bluexrider on 2011-12-03
try changing the server. go to synaptic or package manager >under settings>repositories> where it says Download from: change it to Other then select best server

---

### Post by prashant.g on 2011-12-07
It's not working when i select for best server, after checking it's giving error that 'No suitable download  server found' what should i do now?
I'm new to ubuntu, i don't know how to fix the server. can you please tell me what should i do now??

---

### Post by CMXILies on 2013-01-09
I just installed 10.1 on a Gateway laptop and I am having the same problem. I can't download updates or anything else from the repositories.

---

### Post by oldos2er on 2013-01-09
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

