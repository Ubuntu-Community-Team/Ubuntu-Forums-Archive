---
title: "Mobile bradband"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Okami on 2009-10-12
Posting my problem here too, I hope it is okay even if it is not a problem with only Karmic, I have this problem in Jaunty too. Delete the thread if it should not be here. I will stop nagging about this after this thread. =)

I have a strange problem with mobile broadband and Ubuntu. I hoped it would get better in Karmic but it does not. The problem is that my mobile bradband works sometimes and sometimes not and when it works it does so for a short time or stop working if I try to update or download anything. It does not disconnect it just stop working and when it happens it is almost impossible to get a working connection again. Other times it can work perfectly.

My computer is a LG r405 and there is an integrated modem: Sierra Wireless MC8755. I share this computer with the rest of the family and they do not want me to buy a dongle to use the mobile bradband card with.

Thanks in advance!

Here is my other thread: [http://ubuntuforums.org/showthread.php?p=8087499](http://ubuntuforums.org/showthread.php?p=8087499)

---

### Post by jfernyhough on 2009-10-12
A lot of network problems have been ironed out with updates to Network Manager and to the kernel. You will need to update somehow - could you borrow someone's WiFi, for example?

As an example, my ZTE MF627 needed a lot of coaxing on Jaunty, worked sporadically earlier on in Karmic development, but is now pretty decently ticking along.

---

### Post by Okami on 2009-10-12
Thank you for your answer. I have been downloading (from my Vista partition) Karmic daily live and reinstalled now and then to get updates.

I have searched on Internet but no one else seem to have this problem. Or is everyone with mobile broadband trying for 30 minutes to get a 5 minutes working connection :)

My old computer had problems with some file called DSDT, but it should not be the problem here?

It feels heavy to just wait for this to be solved with future updates :(

---

### Post by Okami on 2009-10-12
I finally found a forum post with a similar problem:

[http://forums.opensuse.org/network-internet/wireless/413740-strange-sierra-usb-modem-problem-11-1-a.html](http://forums.opensuse.org/network-internet/wireless/413740-strange-sierra-usb-modem-problem-11-1-a.html)

The second last post says to add the following lines to /etc/ppp/options
ipcp-max-configure 30
ipcp-max-failure 20

I looked in /etc/ppp/options and found two lines like this:
#ipcp-max-configure <n>

and

#ipcp-max-failure <n>

Should I edit those lines or just add the new ones somewhere? Does anyone know what those lines do? I am a little afraid to add them :oops:

Thanks in advance!

---

### Post by francsal on 2009-10-12
> **Okami said:**
> I finally found a forum post with a similar problem:

[http://forums.opensuse.org/network-internet/wireless/413740-strange-sierra-usb-modem-problem-11-1-a.html](http://forums.opensuse.org/network-internet/wireless/413740-strange-sierra-usb-modem-problem-11-1-a.html)

The second last post says to add the following lines to /etc/ppp/options
ipcp-max-configure 30
ipcp-max-failure 20

I looked in /etc/ppp/options and found two lines like this:
#ipcp-max-configure <n>

and

#ipcp-max-failure <n>

Should I edit those lines or just add the new ones somewhere? Does anyone know what those lines do? I am a little afraid to add them :oops:

Thanks in advance!

I think you can safely remove the "#" symbol before the lines you´ve already found, and add the specific parameters found on the other thread, and see if it works.

Cheers.

Frank.

---

### Post by Okami on 2009-10-13
Internet has been working without problem since I added the lines, I hope it will continue to work. :)

---

