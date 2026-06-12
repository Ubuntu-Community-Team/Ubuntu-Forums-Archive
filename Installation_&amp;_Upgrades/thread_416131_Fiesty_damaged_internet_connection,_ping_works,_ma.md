---
title: "Fiesty damaged internet connection, ping works, mail and Firefox don't"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Patrick K on 2007-04-20
After two days of fighting getting Fiesty installed, it is finally running. However, I have several problems one of which I'll address here.

I can't connect to the internet with Firefox or Thunderbird. I also cannot connect with FireFox to my router. **However, I can ping this site and all the others I tried.** Booting Edgy and Windows, both apps work fine. I looked through the network applet but found nothing there that I could see caused the problem. I went through both TB's and FF's preferences but didn't find anything that I recognized as a problem spot. 

What will it take to get online with Fiesty?

<edit> Seems Firestarter was set to block all outgoing traffic. Strange that it let pings through.

---

### Post by Piviul on 2007-04-21
> **Patrick K said:**
> [...cut...]
I can't connect to the internet with Firefox or Thunderbird. I also cannot connect with FireFox to my router. **However, I can ping this site and all the others I tried.** Booting Edgy and Windows, both apps work fine. I looked through the network applet but found nothing there that I could see caused the problem. I went through both TB's and FF's preferences but didn't find anything that I recognized as a problem spot. 

The same happens to me! I can ping an internet site but firefox can't browse it, I can ping my router but Firefox can't browse it (a little notice: I can reach my router using telnet...)... but I have an exception: google seems to work pretty well. I can ping my pop mail address but thunderbird can't contact it. It's a very strange trouble and I'm getting crazy about it.

> **Patrick K said:**
> 
<edit> Seems Firestarter was set to block all outgoing traffic. Strange that it let pings through.

:( I've no firestarter installed... and iptables -L say that I have non iptables rules installed and all the default policies are "accept".

Piviul

---

### Post by bullgr on 2007-04-21
after upgrading to feisty the iptables scripts i use successful in breezy, dapper and egdy, are not working now.
i believe that the iptables rules are not saved, remains the default rules and so i can't enable samba rule.

something must changed in the new iptables version and my scripts are not working now.

if someone can help, go there to see the iptables scripts
[http://ubuntuforums.org/showthread.php?t=416590](http://ubuntuforums.org/showthread.php?t=416590)

thank's...

---

