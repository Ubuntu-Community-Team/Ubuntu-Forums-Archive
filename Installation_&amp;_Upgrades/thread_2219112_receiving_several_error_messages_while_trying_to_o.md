---
title: "receiving several error messages while trying to operate Lubuntu 14.04"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2014-04-23
Lubuntu 13.10 ran perfectly. No problems at all. Trying to operate Lubuntu 14.04 has been quite challenging. Downright frustrating. I was able to successfully block both Bluetooth and IVP6 in Lubuntu 13.10. However applying the same changes to Lubuntu 14.04 leaves me with several error messages upon boot or a black screen with cursor. I can't even rectify the changes via Grub. I have to completely start over-reformat and reinstall. I have done this 5 times. The sixth time I got the following error message upon booting to desktop and accessing LXTerminal, even before doing anything:

sudo: command not found

sudo leafpad: command not found

sudo apt-get: command not found

I also get the same error messages when accessing root from the Grub menu in recovery mode

I utilized the following to disable Bluetooth and IVP6 in 13.10. Apparently this does not work in 14.04:

sudo leafpad /etc/modprobe.d/blacklist.conf

blacklist ipv6
blacklist rfcomm
blacklist bnep
blacklist btusb
blacklist bluetooth

sudo leafpad /etc/modprobe.d/bad_list
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

sudo leafpad /etc/modprobe.d/blacklist-rare-network.conf
#Disable bluetooth
alias net-pf-31 off

A couple of times I got error messages upon boot that states "bypassing" the entries but then the computer just freezes at that screen. The three other times I just got a black screen with blinking cursor. Can't do anything but a cold reboot. Nothing works. No mouse no keyboard. Once rebooted can't do anything in Grub recovery mode either because of the 'command not found' error message as stated above. Very frustrating.

Lubuntu 13.10 worked terrific. Fast and effective. No problems at all. I just wish I could get Lubuntu 14.04 to work at all.

If anyone can be of any assistance I would greatly appreciate the help. I am very frustrated right now.

Thank you in advance. I hope I can get Lubuntu 14.04 to work as good as Lubuntu 13.10 did for me.

I did check the md5hash and it matched 100%. I can install Lubuntu 14.04 I just can't seem to get it to operate without getting a black screen with cursor or error messages. It is even further frustrating not being able to correct any of the possible errors via Recovery Mode.

---

### Post by ian-weisser on 2014-04-25
The exact details of those boot error messages may be very useful.
Look in /var/log/syslog and /var/log/dmesg for more boot error messages.
If you can't find them, then take a picture and hand-copy the exact error messages here.

---

### Post by steeldriver on 2014-04-25
It sounds like a sequence of sudo commands (rather than the **result** of a sequence of sudo commands) got copied into one of your config files - possibly one of the /etc/modprobe.d files?

---

### Post by roler2 on 2014-04-26
Thank you very much to both of you for your advice and guidance. I went ahead and reformatted and reinstalled and did not blacklist anything and stayed away from changing anything in the modprobe.d folder. Those particular error messages have now disappeared although I cannot stop Bluetooth and IVP6 from running. Maybe that has something to do with the kernel?

The problem I am having now I posted in the Desktop environment section. If you right-click on any Program entry in the Start Menu you have your choice of "Add To Desktop" and "Properties". When you click on "Properties" nothing happens. In fact the whole Start Menu freezes. This also happened when trying Lubuntu without installing. After I finished installing all the updates, the "Properties" option completely disappeared, leaving only the "Add To Desktop" option.

Lubuntu 13.10 ran beautifully. In 13.10 I was able to blacklist Bluetooth and IVP6 via modprobe.d and access the said Start Menu Properties option without any problems. I wish I could get Lubuntu 14.04 to run just as good.

---

### Post by sudodus on 2014-04-26
I suggest that you stay with Lubuntu 13.10, it has 3 more months to go until end of life. We can expect that the new version, 14.04 LTS, will be debugged and polished during those months, so that the new Lubuntu will work a lot better. And this is the first long time support version, so it has the potential to be further improved during 3 years (until April 2017).

Alternatively, if you enjoy debugging and running 'bleeding edge' software, please join the Lubuntu community. See these links

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
[https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)
[https://help.ubuntu.com/community/Lubuntu](https://help.ubuntu.com/community/Lubuntu)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by roler2 on 2014-04-27
Thank you for your input! Unfortunately I have already erased Lubuntu 13.10 from the Disc and burned 14.04. If you can help me with the issue that I posted in the Desktop Environment secion then I will be fine-**[COLOR=#000000]"[/COLOR][Start Menu right-click &#8220;Properties&#8221; option does not work/missing in Lubuntu 14.04]("http://ubuntuforums.org/showthread.php?t=2219678")[COLOR=#000000]". [/COLOR]**[COLOR=#000000]Apparently I am the only one who is having difficulty accessing the File-Properties option. I can survive without having to blacklist IVP6 and Bluetooth. Do you happen to know where the actual executables located for the Start Menu Program entries, such as Firefox or Audacious? Maybe there is a configuration issue that I can fix manually? I don't understand why I can access Add To Desktop but I cannot access Properties. And after fully upgrading, the Properties option completely disappeared. So I am thinking that maybe there is a configuration issue within the Start Menu that I may be able to manually fix. If you can be of any assistance I would very much appreciate the help.

In terms of running Daily Builds, I don't have near the experience to help out although someday I would like to do so. But I will keep the option in mind! Thank you again!


[/COLOR]

---

### Post by sudodus on 2014-04-27
I think this is one of the unsquashed bugs, that might be squashed after 2-3 months. It does *not* work for me either, so you are not the only one. And it is not the only bug. I'm sorry, but I don't know enough to help you. I think we have to wait for the bugs to get squashed. So I repeat the advice, that you stay with Lubuntu 13.10, it has 3 more months to go until end of life (reinstall 13.10 rather than using the 14.04 version that is not serving you well yet).

Depending on your hardware you can also switch to Xubuntu 14.04 LTS if the computer has enough horsepower and RAM, otherwise (with less horsepower or RAM) switch to a light-weight re-spin of Ubuntu 12.04 LTS, for example Bento, Bodhi or LXLE.

---

### Post by sudodus on 2014-04-27
If you take part in the discussions in the Lubuntu mail community, you might get additional help.

Subscribe to [Lubuntu Mailing List]("https://lists.ubuntu.com/mailman/listinfo/lubuntu-users"). Also, please make sure to [read this]("http://www.ubuntu.com/support/community/mailing-lists").

---

### Post by roler2 on 2014-04-27
Thank you again! I think I will re-download and re-install lubuntu 13.10. I was thinking of trying LXLE but I don't know how to download a torrent file. Thank you once again for all of the valuable information. I may join the Lubuntu mail community.

---

### Post by sudodus on 2014-04-27
Lubuntu 13.10 is good.

But I suggest that you learn how to use torrents (which is very useful for downloading linux iso files). Get the torrent file and use it with your bit-torrent client. I use ***Transmission***, and it is activated when I click on the torrent file in a file browser.

You can also start it via a terminal window, change directory to where you have the torrent file, and then (with this example)

```
transmission-gtk LXLE32-12044.torrent
```

---

### Post by roler2 on 2014-04-29
Thank you so much! I really appreciate your advice and guidance! I hope the Lubuntu Community is able to correct the respective issues that are affecting the operation of Lubuntu 14.04. I noticed there are others who are having difficulties with various issues relating to 14.04 so I do hope these specific bugs are eventually resolved.

---

