---
title: "Installing on Dell Latitude X200 - problems"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by admay on 2011-01-02
I think I need some help here as I seem to have exhausted every option I can think of. I have been given a Dell Latitude X200 laptop old, but with a 933MHz processor and 256MB RAM. I want to put some variant of Linux on it so that my youngest niece can have a laptop of her own. 

  If I try to boot from a 10.10 Ubuntu live CD it starts but bombs out with the message “    unable to find a medium containing a live file system”, The same happens with a Xubuntu 10.10 live CD. 

     I have installed both Ubuntu and Xubuntu from the alternate install CD and the install goes fine. However when booting it starts to boot then I get a blank screen and all activity stops. I think that this is when it starts X.

     I have done a server install of 10.10 and I can get a working system with WiFi access to the network. But obviously it doesn’t do much. I have installed X and the xfce desktop but when I issue the startx command I get the blank screen again. If I test X I get a small checkerboard screen with an X cursor in the middle so something is working. 

     Next I tried installing 8.04 – Hardy Heron (Ubuntu – I couldn’t find Xubuntu for 8.04) and all went fine. I had a graphical desktop and wireless worked. So far so good. Ran all the updates and all works fine. 

     I then selected the upgrade option to upgrade to 10.04 – Lucid Lynx, the next LTS release. It downloaded everything over wireless (I have had to switch to WEP encryption because the laptop appears not to support WPA-PSK). Everything installed fine and I got the Lucid Lynx desktop. But now the wireless has stopped working. It can see all the wireless networks in the area but cannot connect. Initially it looked as if the encryption was a problem. It would attempt to connect and then come back and ask for the key again. But I have turned off encryption and it still cannot connect. A direct network connection works fine. 

     So whichever route I take I do not end up with a fully up to date and working system. I kinda suspect that if I can get the live CD to boot and install from that I will still get the blank screen problem so I think that is what I have to concentrate on solving. 

     I have Googled at each stage but seem to find a lot of posts that state the problem with a lot of responses of the ‘I have the same problem’ ilk or others with a WiFi problem where the upgrade is not recognising the hardware.

     So any pointers from those with more experience of this type of thing than me would be gratefully received.

     Andrew

---

### Post by mörgæs on 2011-01-02
With 256 MB memory I would go for Lubuntu rather than Ubuntu/Xubuntu:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261]("http://ubuntuforums.org/showpost.php...&postcount=261")

Here are more light distros:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

If the system freezes, most likely is that you need to apply boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by admay on 2011-01-02
Thanks. I have now tried:

Installing from a Lubuntu live CD. Can boot into the live CD (unlike Ubuntu and Xubuntu) and perform a successful install. Get the full Lubuntu desktop but no wireless - not even anything to tell me that it has wireless installed much less that it can recognise or connect to any networks. There is an icon for wired networks but no mention of wireless. 

Then did a minimal install as per your post. That install detected the wireless card but could not connect so performed the install using a wired connection. Got a successful minimal install with command line. Then installed the Lubuntu desktop using the "sudo apt-get install lubuntu-desktop" command. Rebooted and now back to the blank screen again. 

So looks like the best option is going to be the Lubuntu live CD if I can sort out how to get wireless recognised.

Andrew

---

### Post by mörgæs on 2011-01-02
If you run 

```
hwinfo --netcard
```

you will see which net card(s) you have. Try searching for the card name in these fora; chances are close to 100 % that somebody has already written a solution.

---

