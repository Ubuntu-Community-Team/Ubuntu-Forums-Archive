---
title: "ecryptFS /home directory problem ,vanishing directories, stoping encryption"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by nitinkdhiman on 2012-09-22
Greetings,
My system is Ubuntu 12.04 with kernel 3.2.0-31-generic-pae. 
I also have 10.04 installed. The /home directory is common for both versions of OS.

My problem is with encryption happening of my $home. I did not authorize any encryption policy/paraphrase. Everytime it asked me for a paraphrase, i cancelled the request. 
Currently there is a folder  $HOME/.Private which is almost same size as my $HOME , 91GB. It means my complete $HOME is getting encrypted.
My problem is that some of my folders had started missing! i.e. I can not access them as they are no longer visible in terminal using ls or in file browser. I had 61GB size videos in $HOME/Video but this folder is not visible. In $HOME/.Private there are many files of sizes almost same as my directory. One of them is ECRYPTFS_FNEK_ENCRYPTED.FWbi02S****** is 61GB which is same size as $HOME/Video.

How I can extract this folder back? Yesterday contents of my Download folder also vanished!!! How I can recover my data? How I can stop this encryption?

I am not able to recover using my login password. Although I can mount using my login password. But this mount do not shows all the data (Video folder). Is there some tool to recover the data?

> PC:~/.Private$ sudo ecryptfs-unwrap-passphrase /home/user/.ecryptfs/wrapped-passphrase
Passphrase: 
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs



thanks 
nitin

---

