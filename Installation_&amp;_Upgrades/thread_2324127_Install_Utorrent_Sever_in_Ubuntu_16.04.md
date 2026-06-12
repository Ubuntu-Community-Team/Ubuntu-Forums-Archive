---
title: "Install Utorrent Sever in Ubuntu 16.04"
date: 2016-05-11
forum: Installation &amp; Upgrades
---

### Post by Brij_Raj_Kishore on 2016-05-11
Unable to Install utorrent server in ubuntu 16.04 64 bit.
used tutorial [http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step](http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step).
Was working fine in ubuntu 14.04 but not working in 16.04

---

### Post by howefield on 2016-05-11
Is there a particular part of the tutorial you are stuck on, or maybe an error message. Just to help out the non psychics in here.

---

### Post by Brij_Raj_Kishore on 2016-05-11
1. I have downoaded the utserver from the page [http://www.utorrent.com/intl/en/downloads/linux](http://www.utorrent.com/intl/en/downloads/linux) first link.
2. extract and moved it to ```
/opt
```
3. Then Run [```
sudo chmod -R 77 /opt/utorrent-server-alpha-v3_3/
``` command
4. Then when I run ```
utserver --settingspath /opt/utorrent-server-alpha-v3_3/
```, I got and error
     ```
No command 'utserver' found, did you mean: Command 'ktserver' from package 'kyototycoon' (universe) Command 'ttserver' from package 'tokyotyrant' (universe)utserver: command not found
```

I Think The error is due to permission. When I headed to my```
/opt
``` directory and executed command ```
ls
```,
The```
utorrent-server-alpha-v3_3
``` folder is in green color while all other folders are blue. And then when i tried to enter into the folder by entering ```
cd utorrent-server-alpha-v3_3/
``` it give and error ```
bash: cd: utorrent-server-alpha-v3_3/: Permission denied
```

---

### Post by howefield on 2016-05-13
Is your command in step 3 a typo or really what you entered ?

What worked for me was, after downloading the tarball to the ~/Downloads folder...

```
sudo tar xvzf utserver.tar.gz -C /opt/
```
```
cd /opt/utorrent* && sudo unzip ./webui.zip
```
```
sudo chown -R root:root /opt/utorrent*
```
```
sudo apt-get install openssl
```
```
sudo ./utserver &
```

Then go to localhost:8080/gu in web browser.

---

### Post by Brij_Raj_Kishore on 2016-05-14
Thanks Sir. Your method worked. By the way there was a typo in step 3.
And I think there is also a typo in your last line of reply. Cause [http://localhost:8080/gu](http://localhost:8080/gu) give me invalid request while [http://localhost:8080/gui](http://localhost:8080/gui) worked. And I have 3 questions -:
1. ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo tar xvzf utserver.tar.gz -C /opt/[/FONT][/COLOR]
```  In this code i got everything except ```
-C
```. What does it means here ?
2. Where can i learn these types of commands any book, website etc?
3. How to create a desktop and launcher shortcut of utserver? 
Thanks.

---

### Post by howefield on 2016-05-15
> **Brij_Raj_Kishore said:**
> Thanks Sir. Your method worked. By the way there was a typo in step 3.

And I think there is also a typo in your last line of reply. Cause [http://localhost:8080/gu](http://localhost:8080/gu) give me invalid request while [http://localhost:8080/gui](http://localhost:8080/gui) worked.

You are welcome, glad you got it working and sorry about the typo, just a copy/paste fail missing the last character from my text editor to the forum post.

> sudo tar xvzf utserver.tar.gz -C /opt/ In this code i got everything except -C. What does it means here ?

It means change directory to.. the tarball started in the Downloads folder, -C tells it to extract to a different folder, in this case /opt/.

> Where can i learn these types of commands any book, website etc?

Well, there are numerous ways to learn the command line, I like the man pages, most are well documented and easy to follow. Eg, in your terminal type 

```
man tar
```

Generally you will only need a to commit a few often used options to memory and the man pages are always there to reference the others. Pretty much every command will have a man page. If you don't have a terminal handy for whatever reason, you can browse the man pages in a web browser. 

> How to create a desktop and launcher shortcut of utserver? 

I guess you would want to create a .desktop file in /usr/share/applications/ I'd probably copy the existing firefox .desktop file, rename it, append the URL to the command line, change the icon and place on the launcher.

---

### Post by Brij_Raj_Kishore on 2016-05-16
Thanks Sir.

---

