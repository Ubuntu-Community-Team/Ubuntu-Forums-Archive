---
title: "Updating via Proxy Servers and dial-up"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by gwm on 2007-03-09
Hi,
I think I'm in the right forum. Sometimes I work from behind a proxy server, sometimes from a dial-up modem. I have yet to go home and try out what I think I've learned from this forum over the weekend. This seems to be what I need to do. Is this correct?
Please tell me if my story is wrong, so that I can be spared many hours of trial and error.

**Windows Proxy Logon**
    User Name: usr99
    Password: pwd99
    Logon to: domain99

**Proxy IP and Port**
Ip=192.168.1.1,  port=8080

**1. Firefox**
To switch to using the proxy, setup as follows
    Options -> Network -> Settings
    Click "Manual Proxy Configuration" radio button
    HTTP Proxy -> 192.168.1.1:8080
    Check the box for "Use this proxy server for all protocols"
You will be prompted for user name and password when connecting. Then you enter
    domain99\usr99
    pwd99
in the supplied text boxes and check the save check box.

To switch back to using the direct connection at a later stage, go back to
    Options -> Netwotk -> Settings
    Click "Direct connection to Internet"
The proxy server settings are not discarded and can be reinstated by reselecting th "Manual Proxy Configuration" radio button wwhenever you wish to go back to working through the proxy.

**2. Synaptic Package Manager**
In the network settings, set up the proxy with user login information whereever it wants a proxy server's identification. In this case:
    domain99\usr99: pwd99@192.168.1.1:8080
I'm not in front of an Ubuntu box at the moment, but I think these settings are turned on/off by radio buttons, so that one doesn't need to reenter them each time.

**3. Networking**
Similar to Synaptic.

**4. apt-get**
Edit the file /etc/apt/apt.com to have the line
    Acquire::http::Proxy "true"
Presumably, this must be restored to "false" to work through the dial-up modem again

**5. bash**
Edit /etc/bash.bashrc to contain the following lines
    export htp_proxy=http://domain99\\usr99: pwd@192.168.1.1:8080/
    export ftp_proxy=ftp://domain99\\usr99: pwd@192.168.1.1:8080/
To return to direct connection through the dial-up modem, comment these lines out.
Reinstate them by removing the comment marker when returning to proxy mode.

Phew!!
That seems to be a lot of work every time one changes. Hopefully one doesn't do it too often and then one would need a checklist or something NASA style to ensure that one does them all. Perhaps some of these changes are supposed to happen behind the scenes if one uses the GUI. In my case, Synaptic updates fine, but apt-get doesn't, so the GUI isn't fixing everything. Isn't there a simpler object oriented way where all of this is done in one place?

Please tell me if I have something wrong.
:popcorn:

---

### Post by bapoumba on 2007-03-09
Hello :)

synaptic and apt-get or aptitude read the /etc/apt/apt.conf file for proxy settings. I just overwrite apt.conf with either the proxy setting (work) or the direct setting (home). So you can make it a single step here.

---

### Post by gwm on 2007-03-12
Thanks bapoumba,
Is there some way of commenting out the line in /etc/apt/apt.conf or should one keep two versions of the file on the side and copy the one that is required over the working copy?

I struggled for many hours this weekend.

Whatever else comes of this, my recommendation is that one should not set the proxy manually using the GUI **Administation->Preferences->Proxy Settings**. This must be left as a direct internet connection. Make your changes elsewhere.

What I found doesn't quite gel with your answer. Perhaps the other entries override apt.conf or something. From memory, I ended up with a single line in **/etc/apt/apt.conf** something like

**Acquire::http::Proxy "http://domain99\usr99:Pwd99@192.168.1.1:8081";**

I had to discover that changes to certain files are only recognized after restarting things.
Changes to **/etc/bash.bashrc** mean that you must end your terminal session and restart your testing in a new session. Changes to **Administration->Preferences->Proxy Settings** seem to require a reboot.

I found that a typing error in the ip address of **Administration->Preferences->Proxy Settings** was being reflected in the error messages I was getting from **Synaptic** about the proxy refusing to accept my login. In other words, Synaptic was using these settings to make it's connection, not the ones in apt.conf.

By accident, I found that if **Administration->Preferences->Proxy settings** was set for a direct connection to the internet, then everything else started working beautifully. You see, I had forgotten to change everything else when I activated the dial-up connection. Suddenly the Proxy wasn't denying access any longer. Then I realized that both the telephone modem and the proxy network connection were connected at the same time and the download speeds were *kinda fast* for a phone line.

If I commented out the entries in the **/etc/bash.bashrc** file by putting a # symbol in front of the two **export** lines, apt-get stopped working. So apt-get must have been using those settings and not the one in apt.conf. Perhaps if I remove all the other stuff, including the Synaptics->Preferences->Netwotking and leave only the apt.conf entry it will come right the way you say.

Thanks again,
gwm

---

### Post by bapoumba on 2007-03-12
> **gwm said:**
> 
Is there some way of commenting out the line in /etc/apt/apt.conf or should one keep two versions of the file on the side and copy the one that is required over the working copy?
you can comment adding a # at the beginning of a line. I have two copies of the file.
There is a bug filed : [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/56655]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/56655")
and synaptic/apt-get/aptitude should read the global proxy settings...
> **gwm said:**
> 
What I found doesn't quite gel with your answer. Perhaps the other entries override apt.conf or something. From memory, I ended up with a single line in **/etc/apt/apt.conf** something like

**Acquire::http::Proxy "http://domain99\usr99:Pwd99@192.168.1.1:8081";**
This is similar to my _work proxy setting in apt.conf.
> **gwm said:**
> 
I had to discover that changes to certain files are only recognized after restarting things.
Changes to **/etc/bash.bashrc** mean that you must end your terminal session and restart your testing in a new session. Changes to **Administration->Preferences->Proxy Settings** seem to require a reboot.
Try to close the terminal window and open a new one, see if it helps.
> **gwm said:**
> 
in the **/etc/bash.bashrc** file by putting a # symbol in front of the two **export** lines, apt-get stopped working. So apt-get must have been using those settings and not the one in apt.conf. Perhaps if I remove all the other stuff, including the Synaptics->Preferences->Netwotking and leave only the apt.conf entry it will come right the way you say.

I do not have anything set up in **/etc/bash.bashrc**. Would you have a proxy set up in **/etc/environment** ?

---

### Post by gwm on 2007-03-13
Hi,
I'm sorry that my menu routing has been all wrong. I'm not near the Ubuntu box when I have opportunities to connect to the forum, so I'm working from memory. What you call the *global proxy settings* is probably what I was referring to with the menu path to these settings. My path should have read **Settings->Preferences->Proxy Settings**.

At any rate, I cleared all the settings I had made as a consequence of other forum threads and came up with the following setup that follows your guidelines and works like a charm.

[B]
Global Proxy settings .... Do not set proxy manually. Leave this as a direct internet connection.
Synaptic ....................... Do not set proxy manually. Leave this as a direct internet connection.
/etc/bash.bashrc .......... Do not set proxy manually. Leave this file alone.
/etc/apt/apt.conf
.... Direct dial-up connection .... clear the file.
.... Proxy connection ................ insert a line in the following format

Acquire::http::Proxy "http://domain99\usr99:Pwd99@192.168.1.1:8081";
[/B]
Thanks bapoumba, this sure is a much neater and cleaner setup than I started with.
gwm
:KS 
P.s. cute avatar!

---

### Post by bapoumba on 2007-03-13
> **gwm said:**
> Hi,
I'm sorry that my menu routing has been all wrong. I'm not near the Ubuntu box when I have opportunities to connect to the forum, so I'm working from memory. What you call the *global proxy settings* is probably what I was referring to with the menu path to these settings. My path should have read **Settings->Preferences->Proxy Settings**.
Yes, sorry. Some applications will use these, actually (epiphany web browser, IM or IRC applications, liferea rss reader, evolution mail, sound juicer...). You may not use any of these applications, but I use liferea from work, for ex (and the proxy prohibits any IM o IRC protocol).

> **gwm said:**
> 
[B]
Global Proxy settings .... Do not set proxy manually. Leave this as a direct internet connection.
Synaptic ....................... Do not set proxy manually. Leave this as a direct internet connection.
/etc/bash.bashrc .......... Do not set proxy manually. Leave this file alone.
/etc/apt/apt.conf
.... Direct dial-up connection .... clear the file.
.... Proxy connection ................ insert a line in the following format

Acquire::http::Proxy "http://domain99\usr99:Pwd99@192.168.1.1:8081";
[/B]
Thanks bapoumba, this sure is a much neater and cleaner setup than I started with.
gwm
:KS 
P.s. cute avatar!
I basically have the same settings (except I use the global settings in > System > Prefs > Network proxy).

For apt.conf, I have two files, I overwrite apt.conf with either one, depending from where I am connected:
```
 cat /etc/apt/apt.conf_maison 
ACQUIRE {http::proxy "direct"};
cat /etc/apt/apt.conf_univ 
ACQUIRE { 
http::proxy "http://myproxy.mydomain.fr:myport"
};

```
To overwrite the file :
```
sudo cp /etc/apt/apt.conf_xxx /etc/APT/apt.conf
```
where xxx stands for "maison" (home) or "univ".

I am sure a script to make this an automatic procedure can be written, but I have not bothered as I also switch from ethernet to wifi, from static IP to DHCP and such.

---

