---
title: "Can't upgrade firefox"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by Mevioso on 2012-10-23
Hi :). I am completely new to Ubuntu and do not know much about it. I have been using it for a couple of months. I could go on tumblr. But, recently, I put my log in details and it doesn't go past the log in screen. I figured this must be due to the fact that my firefox version needs an upgrade. Sso, I downloaded the firefox but I don't know what to do after that! Help me please :(

---

### Post by vandorjw on 2012-10-23
What version of firefox do you currently use?

Open a terminal and type:
```

firefox --version

```

I seriously doubt the version of firefox is the problem.


**If you really wish to run the very latest version of firefox, then do this**

In a terminal, type:

```

sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox

```

and press enter after each line

---

### Post by Mevioso on 2012-10-25
All right, it  says I have the latest version. How can I fix the problem then? :( 
When I go onto update manager, it says: New Ubuntu release '11.10' is available. When I click on upgrade, it works fine up until it reaches: installing the upgrades. An error message comes up showing this: The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far have been kept. Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-cookies-perl/libhttp-cookies-perl_6.00-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libh/libhttp-cookies-perl/libhttp-cookies-perl_6.00-2_all.deb) 404  Not Found [IP: 91.189.92.202 80]


Help???
Thanks

---

### Post by dino99 on 2012-10-25
Looks like your internet connection is not stable. With such case you only can wait for better time and/or warn your isp. Have you a monthly limited download volume ?

---

### Post by vandorjw on 2012-10-25
Hey 

Your very first sentence 
> 
I am completely new to Ubuntu


made me believe you acquired ubuntu very recently.
What version of Ubuntu do you have?

You can find this out by opening a terminal and typing 

```

lsb_release -a

```

and post the result back in this thread.

The reason I am asking this is because:
If you are using ubuntu version 11.04, it has reached its End-Of-Life and will no longer be supported.

Refer to [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you have to upgrade, not many people will recommend using the update-manager.
You will have much less of a head-ache if you download a new-version, backup all your personal files, (music, documents, pictures, etc) and re-install ubuntu via CD/DVD.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Mevioso on 2012-11-01
Hii. My version is Ubuntu 11.04. It still works. However, I really want to go on tumblr. could you tell me what I can do? 

Thanks

---

