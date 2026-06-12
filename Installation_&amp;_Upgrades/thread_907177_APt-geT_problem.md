---
title: "APt-geT problem"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by mjunaiddar on 2008-09-01
Hi This is my post that I just wrote in the "Absolute Beginner Talk" section but am not getting any help ther so I think may be some one here can help me :

I am totally new to kubuntu, I was dreaming if I would ever be able to install some packages at mu KUbuntu system installed via the live CD within the Windows XP right. Now the issue is here that after a fresh install and configuring my network settings I tried to install MySQL using apt-get, "sudo apt-get install mysql-server" this is the command I searched from google, but it failed saying mysql-server not found ..... 
 
 some forum says i have to run "sudo apt-get update" and then it will run but when i run it the following errors come:
 
 sudo apt-get update
 Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
 Could not resolve 'us.archive.ubuntu.com'
 Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
 Could not resolve 'us.archive.ubuntu.com'
 Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
 Could not resolve 'us.archive.ubuntu.com'
 Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
 Could not resolve 'us.archive.ubuntu.com'
 ......
 Could not resolve 'us.archive.ubuntu.com'
 Reading package lists... Done
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...dy/Release.gpg) Could not resolve 'us.archive.ubuntu.com'
 
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
 
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
 ........
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
 
 W: Some index files failed to download, they have been ignored, or old ones used instead.
 W: You may want to run apt-get update to correct these problems
 
 
 NOTE I have omited some text to shorten the lenth of the post.
 
 I would highly thankful to u all if i get a reply very very quick 
 
 A detailed one will be more good  as m very very new to linux world
 
 Regards
 Junaid

---

### Post by WakkiTabakki on 2008-09-01
From the error messages it seems like you don't have a working internet connection... 

If you bring up a browser, can you connect to a site? (Obviously I'm guessing you wrote the post from either another computer or a different OS :D )

/N

---

### Post by mjunaiddar on 2008-09-01
yes yes I have the internet which I am using right now replying to u ppl

---

### Post by ThaRabbit on 2008-09-01
I have had the problem before on my server after a reconfigure of my network, it seems the DNS value in a config file doesn't get updated.

do:
```
sudo gedit /etc/resolv.conf
```

and check the ip after "nameserver"

That value should be the same as the Primary DNS ip you get when you pull up your network information (by right clicking the network manager applet in your taskbar and select connection information)

Could you also post a link to your topic in the absolute beginners section?

---

### Post by mjunaiddar on 2008-09-01
> **ThaRabbit said:**
> I have had the problem before on my server after a reconfigure of my network, it seems the DNS value in a config file doesn't get updated.

do:
```
sudo gedit /etc/resolv.conf
```

and check the ip after "nameserver"

That value should be the same as the Primary DNS ip you get when you pull up your network information (by right clicking the network manager applet in your taskbar and select connection information)

Could you also post a link to your topic in the absolute beginners section?

ohh it seems like working now :), Actually the IP for my Gateway was OK at the "/etc/resolv.conf" file but was not correct at the network manager .... I just changed that and its working now .... Many Thanks :)

Best Regards
Junaid

---

### Post by manishtech on 2008-09-02
Please mark this thread as marked..... SO that others can know that it contains some information :)

---

### Post by sar.vivek on 2010-01-10
I am using KUbuntu 9.10.
I am Ubuntu user from last 2 years. But previously I was using Gnome. But this time I tried KUbuntu .. 

And now I am facing the problem with apt-get.
Here is code : 
sudo apt-get update 



Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_IN                                                           
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_IN                                                     
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_IN                                                       
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_IN                                                     
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                                                              
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_IN                                                   
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_IN                                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_IN                                               
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN                                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                                                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_IN                                                  
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_IN                                            
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_IN                                              
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_IN                                            
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Reading package lists... Done                                                                                                                                                                   
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]                                                                                                                                                                                              
                                                                                                                                                                                                
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


I am behind proxy. But that may not be the problem cause my internet connection is working fine. 
I tried various servers for sources. But giving same error for all.

---

