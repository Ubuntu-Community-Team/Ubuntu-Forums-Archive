---
title: "Upgrade problems"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by yngvrr on 2008-04-21
Hello. 
earlier tonight I tried too upgrade from 6.06 to 8.04..
The download of the actual upgrade went well and all.. However after that I had 425 updates.. And I cant get them to upgrade... Im not really god with computers so I called my uncle, who is a programmer and Linux user, and after an hour and a half on the phone we were not there... 
The thing is when I try to upgrade there are "broken files" or corrupted files... for better undarstanding this is the case : 
"E: The package index files are corrupted. No Filename: field for package foomatic-db."
This however is only the case with this command : "sudo apt-get upgrade" 
Ive tried I think most commands that I can possibly do and always with similar outcome...
If I try to skip that file, that is "foomatic-db" via synap. than I get other corrupted files that might surely be coused be dependency however Im not sure because.. as I said Im not really god with computers... 
Has anyone else encountered this problem before? or does anyone know perhaps how to  get over it??

---

### Post by Pumalite on 2008-04-21
I find that the best results are obtained with a clean install. You could save your data and home and try that.

---

### Post by nik1990 on 2008-08-29
I find that the best results are obtained with a clean install. You could save your data and home and try that.

---

### Post by Oldsoldier2003 on 2008-08-29
This thread has been cleaned up to remove spam from a user misguidedly thinking it is acceptable to spam a support thread with useless comments to raise his post count.

I would like to take this moment to remind everyone that post count isn't what is important- the quality of help here on the forums IS the important issue. Spamming support threads in order to raise your post count is completely unacceptable and will be met with a not so nice response. Please continue to report these threads if you see them.

Regards,
OS

---

### Post by sivaprasadreddy on 2008-11-07
Hello sir,

I'm using ubuntu 8.04 version.

I'm trying to upadate my ubuntu using the command: sudo ap-get update

but i'm getting  problem like:

Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN        
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN       
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg     
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN                  
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Reading package lists... Done                          
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems










please help me as early as possible.

---

