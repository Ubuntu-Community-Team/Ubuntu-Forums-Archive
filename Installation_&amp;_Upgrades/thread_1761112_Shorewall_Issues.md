---
title: "Shorewall Issues"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by Hayes43 on 2011-05-17
Hello: I have used these instructions to install Shorewall Firewall. 

They fail each time.

Any advice would be very much appreciated.

[FONT=Arial]Install a Firewall[/FONT]
[FONT=Arial]We now are going to lock down our server a bit more by installing Shorewall, a command-line firewall. To install it[/FONT]
**[FONT=Arial]sudo aptitude install shorewall[/FONT]**
[FONT=Arial]By default, Shorewall is installed with no rules, allowing complete access. However, this is not the behavior we want.[/FONT]
[FONT=Arial]Instead, we’re going to block all connections to anything other than port 80 (HTTP) and port 22 (SSH). First, copy the configuration[/FONT]
[FONT=Arial]files to the Shorewall directory:[/FONT]
**[FONT=Arial]sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/[/FONT]**
[FONT=Arial]Now, open the “rules” file:[/FONT]
**[FONT=Arial]sudo nano /etc/shorewall/rules[/FONT]**
Thanks again

Hayes43

---

### Post by gsmanners on 2011-05-17
So, how exactly does it fail?

---

### Post by Hayes43 on 2011-05-18
When I use this command **[FONT=Arial]sudo aptitude install [COLOR=#ff0000]shorewall[/COLOR][/FONT]**
I receive this. O Packages upgraded, O newly installed, O not upgraded.

When I use this command [FONT=Arial][B]sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/.
[/B] I get this message. CP-cannot stat  no such file or directory

The last command brings up a blank page in the text editior.

Thanks for your advice

Hayes43[/FONT]

---

### Post by gsmanners on 2011-05-18
> **Hayes43 said:**
> When I use this command **[FONT=Arial]sudo aptitude install [COLOR=#ff0000]shorewall[/COLOR][/FONT]**
I receive this. O Packages upgraded, O newly installed, O not upgraded.

When I use this command [FONT=Arial][B]sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/.
[/B] I get this message. CP-cannot stat  no such file or directory

The last command brings up a blank page in the text editior.

Thanks for your advice

Hayes43[/FONT]

First of all, you probably already have it installed (in particular, if the first message told you "shorewall is already the newest version."). It helps me if you can give me the complete responses to these commands. Otherwise, I can't really help you, as I may be missing vital clues.

Secondly, that next command won't work. Maybe they meant for you to perform:

```
sudo cp /usr/share/doc/shorewall/examples/one-interface/* /etc/shorewall/.
```

The third command should work at that point.

---

### Post by Hayes43 on 2011-05-18
When I use this command: [B]sudo aptitude install shorewall
[/B]No packages will be installed, upgraded or removed.
O packages upgraded, O newly installed, O to be removed and upgraded.
Need to get OB of archives, after unpacking OB will be used.
 
When I use this command sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/.

 CP-cannot stat. /user/share/doc/shorewall-common/examples/one-interface/* : 
 no such file or directory
sudo nano /etc/shorewall/rules

This last command brings up a blank page in the text editior.

Top left hand corner                    Top Right Corner                                                        
GNU nano 2.26                             File: etc/shorewall/rules
Blinking cursor.
At the bottom of the  page there are several commands that I can use to exit, cancel etc.

Here is the web URL I am following to install this server
 
[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
Hope this is more helpful
Hayes43

---

