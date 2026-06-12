---
title: "cannot do apt-get install after installing hardy heron"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2008-05-25
I just installed ubuntu 8.04 on my computer at work 
(I successfully installed ubuntu on my home machine).

I can access the internet via Firefox with this intallation
as in that's how I'm making this post.
However I cannot do an apt-get install or an apt-get update
from my machine.

When I try something like:
                  
              sudo apt-get install lyx

I get:   "E Couldn't find package lyx"

When I try: 
 
             sudo apt-get update

I get a long list of errors such as:

            Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
               Could not connect to  MyHostName:80 (127.0.1.1).  (111 Connection refused)

or:

         W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2)  Could not connect to MyHostName:80 (127.0.1.1). - connect (111 Connection refused)

Some possible sources of problems:

   During installation I was asked for an internet address.
I didn't know what setting to use to I left it blank.
   During Installation I was asked for HTTP proxy information.

   It requested information of the form:
     [http://[](http://[)[user][:pass]@]host[:port]

   I answered with:   "MyHostName"

Assuming to solve this I must set my Internet address
how do I do this?

 If I must give a different value for the HPPT proxy
 what value am I supposed to give?

 If my problem is elsewhere where is my problem?

Thanks in advance for any advice.

Ralph Boland

---

### Post by DonThompson on 2008-05-26
I have a similar issue, but with the server so no Firefox.  I can ping by IP address but not by name; though other (windows & Ubuntu) machines with identical ifconfig results can do both.  Apt-get install always gets me "couldn't find package".    The first installation I had set to include a DNS server, but thought that might be the issue, so the re-install does not have that option selected, but no go. 

It really seems to be the networking, but I can't fix that either.

---

### Post by DonThompson on 2008-05-27
It was DHCP.  By providing the machine its IP address, subnet mask and gateway (editing /etc/network/interfaces) things seem to be working now.  Also went to edit /etc/resolv.conf but it already had the same DNS names as the rest of the computers - got 'em from DHCP, I suppose, so I just saved it.  A reboot and it could resolve domain names and do sudo apt-get.

Soon I'll have a second Ubuntu server with a GUI to go with my 5 windows ones.  If it does what I want it to do, they'll all slowly but surely migrate to Ubuntu...  With GUIs.

---

### Post by iaculallad on 2008-05-27
> **Ralph Boland said:**
> I just installed ubuntu 8.04 on my computer at work 
(I successfully installed ubuntu on my home machine).

I can access the internet via Firefox with this intallation
as in that's how I'm making this post.
However I cannot do an apt-get install or an apt-get update
from my machine.

When I try something like:
                  
              sudo apt-get install lyx

I get:   "E Couldn't find package lyx"

When I try: 
 
             sudo apt-get update

I get a long list of errors such as:

            Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
               Could not connect to  MyHostName:80 (127.0.1.1).  (111 Connection refused)

or:

         W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2)  Could not connect to MyHostName:80 (127.0.1.1). - connect (111 Connection refused)

Some possible sources of problems:

   During installation I was asked for an internet address.
I didn't know what setting to use to I left it blank.
   During Installation I was asked for HTTP proxy information.

   It requested information of the form:
     [http://[](http://[)[user][:pass]@]host[:port]

   I answered with:   "MyHostName"

Assuming to solve this I must set my Internet address
how do I do this?

 If I must give a different value for the HPPT proxy
 what value am I supposed to give?

 If my problem is elsewhere where is my problem?

Thanks in advance for any advice.

Ralph Boland

Are you using DHCP? Try entering this on the terminal and post whatever result it pops out.

Code:

> ifconfig eth0

Or (given the setting that you can connect to the net) try enabling the software repositories. System->Administration->Software Sources and make sure that Main, Universe, Restricted, Multiverse under the "Ubuntu Software" tab is enabled. Uncheck installable from CD-ROM/DVD check box then click on close button.

On the terminal do this:

Code:

> sudo apt-get update

then try to install lynx.

---

### Post by skyv.ism on 2008-05-31
[SIZE="4"][COLOR="Red"]I am new to ubuntu.I have just install ubuntu 8.04 hardy heron.I am not able to install any software.Tried to update apt-get,but failed.
       
 I replaces etc/apt/sources.list with the following and tried to update it,but not succeeded.what I do now?[/COLOR][/SIZE]:(


[B]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
[/B]

---

### Post by Partyboi2 on 2008-05-31
[QUOTE]> **skyv.ism said:**
> [SIZE=4][COLOR=Red]I am new to ubuntu.I have just install ubuntu 8.04 hardy heron.I am not able to install any software.Tried to update apt-get,but failed.
       
 I replaces etc/apt/sources.list with the following and tried to update it,but not succeeded.what I do now?[/COLOR][/SIZE]:(

If you are using hardy you will need a hardy sources.list not a gusty one. So you will need to replace the gusty sources.list with a hardy sources.list.

---

### Post by skyv.ism on 2008-05-31
[COLOR="Red"][SIZE="4"]How can I get hardy source list? I tried to replace all gusty by hardy in the source list in 1st message,but  it didn't work.[/SIZE][/COLOR]

---

### Post by Partyboi2 on 2008-05-31
> **skyv.ism said:**
> [SIZE=1][COLOR=Red]How can I get hardy source list? I tried to replace all gusty by hardy in the source list in 1st message,but  it didn't work.[/COLOR][/SIZE]
Replace the old sources.list with the one below.
Open a terminal (Applications>Accessories>Terminal) 
```
gksudo gedit /etc/apt/sources.list
```delete the contents and copy and paste this one.

```
 #deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu hardy-updates restricted main multiverse universe

```After you have saved the new one, in the terminal  type
```
sudo apt-get update
```

---

### Post by skyv.ism on 2008-06-01
[COLOR="Red"][SIZE="4"]Still I face the problem below after "sudo apt-get update" in the the terminal.[/SIZE][/COLOR]


[SIZE="4"][SIZE="2"]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'[/SIZE][/SIZE]


like these there are more errors and warning.

---

### Post by Partyboi2 on 2008-06-01
"What happens when you change the server to another one? You can do this by opening up Software Sources (System>Admin>Software Sources) On the first tab, look for  "Download from" and select "other" and choose another location.

---

### Post by skyv.ism on 2008-06-01
[SIZE="3"][COLOR="Blue"]Still it is not working. Is there may be any problem with the server, I used proxy server 10.0.200.14

        If this may true then what  I have to do or there are some other problems. [/COLOR][/SIZE]

---

### Post by Partyboi2 on 2008-06-02
Have you configured apt-get to use proxy? You can do this by opening up Synaptic Package Manager (System>Admin>Synaptic Package Manager and click on Settings>Preferences>Network.

---

