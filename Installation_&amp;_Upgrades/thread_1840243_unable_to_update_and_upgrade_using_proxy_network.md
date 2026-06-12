---
title: "unable to update and upgrade using proxy network"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by amirmku on 2011-09-07
Hi,
I am newbie to ubuntu but I was loving it. Recently I moved to  institution where I have to access Internet through proxy network with  given username and password.

The problem is I am unable to update using update manager, even I am  unable to update using terminal. 

Update manger always return a message "connection refused".

I have changed my browser setting to proxy so I am able to access  internet . but unable to update using update manager and even unable to  access internet using terminal.

Not only this I am unable to use Team viewer and social networking  gwibber on my ubuntu 10.04

Please help me out

---

### Post by haqking on 2011-09-07
> **amirmku said:**
> Hi,
I am newbie to ubuntu but I was loving it. Recently I moved to  institution where I have to access Internet through proxy network with  given username and password.

The problem is I am unable to update using update manager, even I am  unable to update using terminal. 

Update manger always return a message "connection refused".

I have changed my browser setting to proxy so I am able to access  internet . but unable to update using update manager and even unable to  access internet using terminal.

Not only this I am unable to use Team viewer and social networking  gwibber on my ubuntu 10.04

Please help me out


You will need to see you Systems Administrator with proxy related issues it is down to the them.

Any other method probbaly invloves circumventing the proxy which i am sure contravenes and Acceptable use Policy for the network.

See the admin/network manager etc and they will tell you how to make the settings to allow it or tell you it is not allowed;-)

---

### Post by ~!geek!~ on 2011-09-07
> **amirmku said:**
> Hi,
I am newbie to ubuntu but I was loving it. Recently I moved to  institution where I have to access Internet through proxy network with  given username and password.

The problem is I am unable to update using update manager, even I am  unable to update using terminal. 

Update manger always return a message &quot;connection refused&quot;.

I have changed my browser setting to proxy so I am able to access  internet . but unable to update using update manager and even unable to  access internet using terminal.

Not only this I am unable to use Team viewer and social networking  gwibber on my ubuntu 10.04

Please help me out

 Try to search for network proxy in dash (in ubuntu 11.04) or system->preference->networkproxy (before 11.04 versions) Set the required fields there!!

---

### Post by amirmku on 2011-09-07
> **~!geek!~ said:**
> Try to search for network proxy in dash (in ubuntu 11.04) or system->preference->networkproxy (before 11.04 versions) Set the required fields there!!

hey tried that, but unable to add add-apt repository for upgrading to firefox6.

---

### Post by haqking on 2011-09-07
> **amirmku said:**
> hey tried that, but unable to add add-apt repository for upgrading to firefox6.


ask your system admin, if you know the proxy settings put them in your global proxy information using system>preferences>network proxy

if you dont know them again see System Admin.

if you are trying to get past a proxy in place then like i said will be against the AUP for network i imagine

---

### Post by amirmku on 2011-09-08
> **haqking said:**
> ask your system admin, if you know the proxy settings put them in your global proxy information using system>preferences>network proxy

if you dont know them again see System Admin.

if you are trying to get past a proxy in place then like i said will be against the AUP for network i imagine

I had applied proxy settings system wide and able to run sudo apt-get update on my terminal. But when I tried adding add-apt repository for firefox6 it returned following error

sudo add-apt-repository ppa:mozillateam/firefox-stable
Error reading [https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-stable:](https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-stable:) <urlopen error [Errno 110] Connection timed out>

---

### Post by haqking on 2011-09-08
> **amirmku said:**
> I had applied proxy settings system wide and able to run sudo apt-get update on my terminal. But when I tried adding add-apt repository for firefox6 it returned following error

sudo add-apt-repository ppa:mozillateam/firefox-stable
Error reading [https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-stable:]("https://launchpad.net/api/1.0/%7Emozillateam/+archive/firefox-stable:") <urlopen error [Errno 110] Connection timed out>


so your orignal problem is solved correct?

now it is a PPA issue and different to your OP ?

that link seems to be down

---

### Post by Toz on 2011-09-08
The firefox ppa is an [COLOR="Red"]https[/COLOR] link. At my work where we have a proxy, I have to specify both http and an https proxy settings to get both protocols to work. Perhaps its the same for you. Since I do most of my work from the command line, I use the following commands to setup my proxies:
```
export http_proxy="http://proxy:port"
export https_proxy="http://proxy:port"

sudo add-apt-repository .........
```

Not sure how you set up your proxy, but is there an option there to include https?

---

### Post by amirmku on 2011-09-09
> **haqking said:**
> so your orignal problem is solved correct?

now it is a PPA issue and different to your OP ?

that link seems to be down

Not sure because updating from update manger returned a error message
"[COLOR=Red]Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check[/COLOR]".

---

### Post by amirmku on 2011-09-09
> **Toz said:**
> The firefox ppa is an [COLOR=Red]https[/COLOR] link. At my work where we have a proxy, I have to specify both http and an https proxy settings to get both protocols to work. Perhaps its the same for you. Since I do most of my work from the command line, I use the following commands to setup my proxies:
```
export http_proxy="http://proxy:port"
export https_proxy="http://proxy:port"

sudo add-apt-repository .........
```Not sure how you set up your proxy, but is there an option there to include https?

I tried ur way but it returned the following error.
amir@amir-laptop:~$ export http_proxy="http://172.141.121.99:8086"
amir@amir-laptop:~$ export https_proxy="http://172.141.121.99:8086"
amir@amir-laptop:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Error reading [https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-stable:](https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-stable:) <urlopen error [Errno 110] Connection timed out>

---

### Post by Toz on 2011-09-09
My bad - sorry I missed this. The proxy won't work with sudo because the proxy settings won't exist in the elevated account environment. Try this:
```
sudo bash
(enter password)
export http_proxy="http://172.141.121.99:8086"
export https_proxy="http://172.141.121.99:8086"
add-apt-repository ppa:mozillateam/firefox-stable
```

---

### Post by pieroxy on 2011-09-16
That fixed it for me. How can one set an environment var that is system wide (or at least, that would be set when sudoing)?

---

### Post by Toz on 2011-09-16
> **pieroxy said:**
> That fixed it for me. How can one set an environment var that is system wide (or at least, that would be set when sudoing)?

Add the proxy commands to your ~/.bashrc file and then:
```
sudo visudo
```
and add below the line:> Default env_reset
line to read:
```
Defaults env_keep += "ftp_proxy http_proxy https_proxy"
```

Log out and back in again.

---

### Post by pieroxy on 2011-09-16
It works great, thanks.

---

