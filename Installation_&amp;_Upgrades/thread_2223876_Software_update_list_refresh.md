---
title: "Software update list refresh?"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by crustacean2 on 2014-05-13
Hello,  This seems like the type of question that probably has been asked a billion times before but I can't seem to find the correct combination of search terms to find it.  The problem is the automatic updates that run flagged some software for update that I don't use, so using Ubuntu software center I uninstalled the software(Gnome control center account plugin for single signon...).  Now, every time the Software updates program runs it pesters me about updating the previously named software despite the fact it has been removed.  Is there a command line command I can issue to get software updates to refresh what needs to be updated?  I am using Ubuntu 13.1 by the way.  Thank you!

---

### Post by grahammechanical on 2014-05-13
So, you want the commands to update/upgrade in a terminal.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by crustacean2 on 2014-05-13
Actually, that is not quite what I want.  Please correct me if I am wrong, but apt-get upgrade will apply all the suggested updates which in this case is for software that has been uninstalled using the software center, and it would seem that apt-get update should work, but it does not.  I tried it yesterday.  I just want the update manager to somehow realize that the software it is suggesting I update is no longer installed.

---

### Post by deadflowr on 2014-05-13
```
sudo apt-get update
```
merely updates the list of available packages.
```
sudo apt-get upgrade
```
only updates packages already existing on the system.

So, if the updater is listing a package to be installed, then chances are something about the package exists on the system.
Be that either a dependency, or the package wasn't fully removed.

---

### Post by slickymaster on 2014-05-13
You can query your system to see it's fully removed or not. In a terminal run:```
dpkg -l | grep account*
```and check your results against [http://packages.ubuntu.com/trusty/gnome/unity-control-center-signon](http://packages.ubuntu.com/trusty/gnome/unity-control-center-signon)

---

### Post by Old_Grey_Wolf on 2014-05-13
Since you are using saucy, find the correct "Gnome control center account plugin for single signon - ..." package at [http://packages.ubuntu.com/saucy/gnome/](http://packages.ubuntu.com/saucy/gnome/) Edit: there are 13 to choose from.

Click on the package and compare its contents as slickymaster said.

---

### Post by crustacean2 on 2014-05-13
Thank you Deadflowr and Slickymaster, here is what I ended up doing:  ```
dpkg -l | grep account*
```   Here is what was returned:  

```
ii  account-plugin-aim                        3.8.4-1ubuntu2                          amd64        Messaging account plugin for AIM  
ii  account-plugin-facebook                   0.11+13.10.20130802-0ubuntu1            all          GNOME Control Center account plugin for single signon - facebook  
ii  account-plugin-flickr                     0.11+13.10.20130802-0ubuntu1            all          GNOME Control Center account plugin for single signon - flickr  
ii  account-plugin-google                     0.11+13.10.20130802-0ubuntu1            all          GNOME Control Center account plugin for single signon  
ii  account-plugin-jabber                     3.8.4-1ubuntu2                          amd64        Messaging account plugin for Jabber/XMPP  
ii  account-plugin-salut                      3.8.4-1ubuntu2                          amd64        Messaging account plugin for Local XMPP (Salut)  
ii  account-plugin-twitter                    0.11+13.10.20130802-0ubuntu1            all          GNOME Control Center account plugin for single signon - twitter  
ii  account-plugin-windows-live               0.11+13.10.20130802-0ubuntu1            all          GNOME Control Center account plugin for single signon - windows live  
ii  account-plugin-yahoo                      3.8.4-1ubuntu2                          amd64        Messaging account plugin for Yahoo!  
ii  accountsservice                           0.6.34-0ubuntu6                         amd64        query and manipulate user account information  
ii  gir1.2-accounts-1.0                       1.14+13.10.20131016.2-0ubuntu1          amd64        typelib file for libaccounts-glib0  
ii  gir1.2-accountsservice-1.0                0.6.34-0ubuntu6                         amd64        GObject introspection data for AccountService  
ii  gnome-online-accounts                     3.8.3-2                                 amd64        GNOME Online Accounts  
ii  libaccount-plugin-1.0-0                   0.1.7~+13.10.20130724.1-0ubuntu1        amd64        libaccount-plugin for GNOME Control Center  
ii  libaccount-plugin-generic-oauth           0.11+13.10.20130802-0ubuntu1            amd64        GNOME Control Center account plugin for single signon - generic OAuth  
ii  libaccount-plugin-google                  0.11+13.10.20130802-0ubuntu1            amd64        GNOME Control Center account plugin for single signon - Google Auth  
ii  libaccounts-glib0                         1.14+13.10.20131016.2-0ubuntu1          amd64        library for single signon  
ii  libaccounts-qt5-1                         1.10+13.10.20131016.1-0ubuntu1          amd64        QT library for single sign on  
ii  libaccountsservice0                       0.6.34-0ubuntu6                         amd64        query and manipulate user account information - shared libraries  
ii  mcp-account-manager-uoa                   3.8.4-1ubuntu2                          amd64        GNOME multi-protocol chat and call client (UOA plugin)  rc  
ii  webaccounts-extension-common              0.5-0ubuntu1                            amd64        Ubuntu Online Accounts browser extension - common files
```

 So I went through the list of what was returned and basically removed anything with the words "GNOME Control Center account plugin for single signon".    Here is an example of what I did to remove the various packages:  ```
sudo apt-get remove account-plugin-facebook
```   If I did get a bit overzealous and broke something, am I correct in assuming the following command will restore any dependencies that may have been needed for any other package?  ```
sudo apt-get check
```  By the way, thank you for the help!

---

### Post by crustacean2 on 2014-05-13
Please forgive the second code tag, for some reason new lines are being removed, isn't the code tag supposed to preserve the formatting as it is?

---

### Post by Old_Grey_Wolf on 2014-05-13
> **crustacean2 said:**
> If I did get a bit overzealous and broke something, am I correct in assuming the following command will restore any dependencies that may have been needed for any other package?  ```
sudo apt-get check
```  By the way, thank you for the help!

```
sudo apt-get check
```
This command is a diagnostic tool. It does an update of the package lists and checks for broken dependencies.
```
sudo apt-get -f install
```
This command does the same thing as Edit->Fix Broken Packages in Synaptic. Do this if you get complaints about packages with "unmet dependencies".

---

### Post by Old_Grey_Wolf on 2014-05-13
> **crustacean2 said:**
> Please forgive the second code tag, for some reason new lines are being removed, isn't the code tag supposed to preserve the formatting as it is?

What you pasted between the code tags did not have new line formatting to preserve.

---

### Post by Elfy on 2014-05-13
edited the dpkg list - hopefully a bit easier to parse now.

---

### Post by slickymaster on 2014-05-14
> **Old_Grey_Wolf said:**
> Since you are using saucy, find the correct "Gnome control center account plugin for single signon - ..." package at [http://packages.ubuntu.com/saucy/gnome/](http://packages.ubuntu.com/saucy/gnome/) Edit: there are 13 to choose from.

Click on the package and compare its contents as slickymaster said.

Good catch, Old_Grey_Wolf. Thanks for alerting the OP that I posted the wrong link (Trusty instead of Saucy), which just goes to show us that four eyes do see better than two.

---

