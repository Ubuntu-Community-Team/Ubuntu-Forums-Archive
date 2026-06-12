---
title: "upgrade - how?"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by bikeman01 on 2012-03-16
i installed 9.04 from cd. 

tried to update to 9.10 and got:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

so i downloaded latest iso and created cd.

when i boot from the cd it wants to do a fresh install.

how do i upgrade? 

ps does it need to be so hard?



this is what i get from

---

### Post by winh8r on 2012-03-16
Ok, 9.04 is the release from April 2009 which is no longer supported, this would have upgraded to 9.10 which was October 2009, again this version is outdated and no longer supported.

Your best option at the moment wuld be to download 10.04.4LTS from here

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")


Back up all your data on your 9.04 installation to an external drive/media and install 10.04.4LTS alongside 9.04 on your hard drive and transfer your data across to the new installation. (the back up is a safety measure in case of any errors or problems, and should be done routinely anyway)

10.04.4LTS is a Long Term Support release and still has another year of support and is very very stable.

The next LTS release will be 12.04 which is due to come out in April this year but is still in beta testing stage so is not recommended for use as your only operating system just yet.

The reason that I am suggesting using 10.04 is that it is stable and also broadly similar to the layout and feel of 9.04 in many ways, whereas the later releases, 11.04, 11,10  are completely different and you would be better to get used to them a little before opting to use them as your primary operating system. You can run them as a live cd and if you choose to opt for them then all good and well.

I just though it might be easier for you to upgrade a stage at a time to prevent too much of a radical change all at once for you.


Hope this helps explain it a bit.

---

### Post by bikeman01 on 2012-03-16
I did a clean install to 11.10 before read your reply.

Now I have now wireless..........

Arrrrrrrrgggggggghhhhhhhh

Why would a newer version of ubuntu drop the broadcom driver?

How do i get wireless to work?

---

### Post by winh8r on 2012-03-17
Did you follow the steps in the other thread you posted to?

[http://ubuntuforums.org/showthread.php?t=1860574&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=1860574&highlight=broadcom")

---

### Post by Mathor on 2012-03-17
It sounds like your internet connection isn't working. I would try connecting to ethernet and running an update, then you should be good as far as wireless goes.

---

### Post by Subidubi32 on 2012-03-17
Try to configure network driver, or I don't know, in the 11.10 my wireless works fine. Or take a look at your router.

---

