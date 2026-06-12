---
title: "F5 Networks Firepass VPN Firefox 15 Plugin Install"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by jamestrowbridge on 2012-09-05
Hello-

I thought I'd share since I've struggled with this all day...

After updating Firefox to version 15 (seems like it was only on 4 a couple weeks ago haha), my F5 Firepass VPN wouldn't work anymore.

The trick is:
[LIST=1]
[*]If you've already tried to install the plugin in FireFox, you'll need to remove it first, close FireFox, then go to '/home/<your username>/.mozilla/firefox/<uniqueString1>/extensions/<uniqueString2>/plugins' and verify that 'np_F5_SSL_VPN_i386.so' is in there (so you have the right extension folder), then just remove the entire '<uniqueString2>' folder (whatever it may actually be called)
[*]Close FireFox
[*]Open FireFox as root ( hit CTRL-ALT-T and type 'sudo firefox' enter your password and hit enter )
[*]Go to your F5 VPN site, log in, try to connect, install the plugin, restart FireFox when prompted
[*]Close FireFox
[*]In the terminal type 'find | egrep plugins/np_F5_SSL_VPN_i386.so'
[*]The above command will return a bunch of rows maybe, you're looking for the one that looks like this './.mozilla/firefox/<uniqueString1>/extensions/<uniqueString2>/plugins/np_F5_SSL_VPN_i386.so'
Using that row's path, enter this in to the terminal 'sudo chmod 777 -R /home/<yourusername>/.mozilla/firefox/<uniqueString1FromAbove>/extensions/<uniqueString2FromAbove>' hit enter
[*]Then open Firefox as normal by clicking on it in the menu and try to connect, this should work with no problem
[/LIST]

I'm sure this can be done in a better way (please post!), but this is the quick way that I did it.  I know that chmod 777 is usually not a good thing, but this is a rather closed system I'm using and it's pretty much only for VPN.  I may change that later by changing groups, etc.  Just wanted to get this out quickly since FireFox 15 is being pushed out in the repos.



Tags that I'm not allow to create:
FireFox 15, F5 Firepass, F5 VPN

---

