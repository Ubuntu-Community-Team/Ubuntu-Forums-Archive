---
title: "Still unable to download updates in Ubuntu 6.10"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by manic34 on 2007-03-11
Hi Everyone,

Can someone please help me !!!

As I am new to Ubuntu I am a little naive but I am having problems with the 'Add/Remove' tab. Everytime I try to download updates, add ons etc the connection times out without having downloaded anything ( this also happens when I try sudo apt-get through terminal. My firefox browser is working fine and I am having no problems surfing or d/loading via my browser, only when I try to use Ubuntu updater I have no joy.

Can anyone offer me some suggestions ??

Many Thanks,
Anthony

---

### Post by Kateikyoushi on 2007-03-11
Could you post the output of the following command ?

```
sudo aptitude update
```

---

### Post by manic34 on 2007-03-11
Hi There,

Thanks for replying, this is the response that I get ... and its still going


Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by Kateikyoushi on 2007-03-11
I saw this once before DNS error, maybe ipv6 you are trying to connect to 1.0.0.0 which is of course not the right IP.

Read this your problem looks the same. [LINK]("http://www.mepis.org/node/10306")

---

### Post by manic34 on 2007-03-11
Hi Again,

thanks for the info though I must admit it means absolutely nothing to me. With a non techie background I am finding some of this info quite a bit daunting. Would you be able to explain to me in laemans terms what I should do. Sorry if I seem dumb but I just dont understand what I should do.

Thanks,
Anthony

---

### Post by Kateikyoushi on 2007-03-11
Open Network Settings, System > Administration > Network there click the DNS tab and the add button.
Type the address 4.2.2.2

Then try to update again.

---

### Post by manic34 on 2007-03-11
Hi,

No joy Im afraid, I added 4.2.2.2 to the DNS servers list and tried to reload in Synaptic Package Manager and it is not downloading anything, it just sits there idle. After some time waiting it tells me that it failed.

---

### Post by Kateikyoushi on 2007-03-11
Okay undo what we tried last time, remove that from the DNS servers list and try another approach.

Step 1) gksudo gedit /etc/resolv.conf add the IP to your ISP if you know them or to OpenDNS (208.67.222.222 and 208.67.220.220). Like "nameserver 208.67.222.222" add one line per server, a maximum of 3 servers. There should already be one IP there, use it as a pattern. Without step 2 this is useless. 

Step 2) gksudo gedit /etc/dhcp3/dhclient.conf 

add a line "prepend domain-name-servers 208.67.222.222,208.67.220.220;" (no quotes) The DNS servers here must be the same as in /etc/resolv.conf. The prepend stops the servers being ditched in etc/resolv.conf

---

### Post by manic34 on 2007-03-11
Whoa .... thats a lotta info.

Ok,  Ive typed gksudo gedit /etc/resolv.conf into terminal and it has changed the prefix to :

nameserver 10.1.1.1

What do I do next ?

---

### Post by Kateikyoushi on 2007-03-11
Add the two Opendns servers as well.

nameserver 208.67.222.222
nameserver 208.67.220.220

Then copy this to terminal

gksudo gedit /etc/dhcp3/dhclient.conf

Add this line to the end.

prepend domain-name-servers 10.1.1.1;208.67.222.222,208.67.220.220;

Save, then try to update again.

---

### Post by manic34 on 2007-03-11
done all that and still no good, no downloads

---

### Post by Kateikyoushi on 2007-03-11
Did you reboot ?

---

### Post by manic34 on 2007-03-11
Yes, just rebooted and tried again. Same result unfortunately ... no downloads

---

### Post by Kateikyoushi on 2007-03-11
Okay then let's remove those

nameserver 10.1.1.1

First from resolv.conf

gksudo gedit /etc/resolv.conf

Then dhclient.conf

gksudo gedit /etc/dhcp3/dhclient.conf

change the line we add before to look like this.

prepend domain-name-servers 208.67.222.222,208.67.220.220;

Save both reboot try again.

There is still one thing what can be done so no need to panic if still not works, actually did not work for me either first time.

---

### Post by manic34 on 2007-03-11
mwa mwa mwa

you are an absolute legend, its downloading now !!!

Though of 76 files that it said were available to d/load, quite a few failed and this is the message that I got at the end

> [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by Kateikyoushi on 2007-03-11
Good to know it worked, then post your sources.list

```
cat /etc/apt/sources.list
```

---

### Post by manic34 on 2007-03-11
OK, I assume I just type that in terminal and then post the results ?

If so, do I have to wait until my computer has finished downloading as it has now decided that there is another 157 items available for download ( this appeared in a light bulb icon alongside the time ) and are currently downloading

Thanks heaps for your help

---

### Post by Kateikyoushi on 2007-03-11
Yes, just copy to terminal when the download finished.

---

### Post by manic34 on 2007-03-11
OK, all the updates d/loaded successfully ..... YIPPEE !!!

this is the response I got> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse #Added by software-properties


---

### Post by Kateikyoushi on 2007-03-11
Edit the sources.list

```
gksudo gedit /etc/apt/sources.list
```

Change the http to ftp in the lines which produce the errors.

Then update again,

---

### Post by pradeepadapa on 2007-03-11
shuld we change all the lines which has http to ftp or only some lines in the sources.lst file.

---

### Post by manic34 on 2007-03-11
Hi Again,

this is what is displayed when I type 

gksudo gedit /etc/apt/sources.list

can you tell me which lines if any have the errors as I am not sure

Thanks again for your help

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse #Added by software-properties

---

### Post by Kateikyoushi on 2007-03-11
I read two solutions to this problem, could not test them myself as I can connect to the servers.

Change the http to ftp, you can change it in all the addresses and it might work, actually for you it makes no difference whether it  is using ftp or http

The other was was to comment all the lines by putting a hash infront of the lines (might be a good idea to put hashes infron of all the lines so your currently commented lines can still be distiguished after the next step) then reboot try to update which of course won't work then remove the hashes from the beginning of the lines and try to update again, so far one person reported that this works.

---

### Post by manic34 on 2007-03-12
Hi,

I changed all the http to ftp and then added comments rebooted, tried again, removed all comments and tried again and the response I got was this

> eb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

### Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse #Added by software-properties

### Uncomment the following two lines to add software from the 'universe'
## repository.
### N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security universe
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse #Added by software-properties
deb [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) edgy-security restricted main universe
deb-src [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) edgy-security restricted main universe #Added by software-properties
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse #Added by software-properties

---

### Post by Kateikyoushi on 2007-03-12
If the beginning of the first line is looks like in your pos add a d to it so it begins with deb. Also uncomment the au mirrors because you already wrote universe in the second line, and add universe to the end of the first line.

Like this

> deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

### Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe multiverse #Added by software-properties

### Uncomment the following two lines to add software from the 'universe'
## repository.
### N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy universe
#deb-src [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy universe

Then try to update again.

```
sudo aptitude update
```

---

### Post by manic34 on 2007-03-12
Ok, just to clarify, once I have made the changes is what you have posted ALL that I should have. ie do I have to delete all the extra information that my screen currently shows ??

Thanks

---

### Post by manic34 on 2007-03-12
Sorry, what I mean is do I delete this info

[QUOTE]deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security universe
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse #Added by software-properties
deb [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) edgy-security restricted main universe
deb-src [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) edgy-security restricted main universe #Added by software-properties
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse #Added by software-properties [QUOTE]

---

### Post by Kateikyoushi on 2007-03-12
No just these two lines. Comment to look like this or delete them I did not post the rest of your sources.list because that was right.

#deb [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy universe
#deb-src [ftp://au.archive.ubuntu.com/ubuntu/](ftp://au.archive.ubuntu.com/ubuntu/) edgy universe

---

### Post by manic34 on 2007-03-12
Ok, did that and ran

sudo aptitude update

this was the result

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports Release.gpg                      
Get:1 [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/main Translation-en_US         
Ign [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/main Translation-en_US           
Get:2 [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/restricted Translation-en_US   
Ign [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/restricted Translation-en_US     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:4 [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/universe Translation-en_US  
Get:5 [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                 
Ign [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:6 [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports Release [44.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                       
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/main Packages               
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/universe Packages
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security Release.gpg
Get:7 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy Release.gpg [191B]
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/main Sources
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/universe Sources
Hit [ftp://au.archive.ubuntu.com](ftp://au.archive.ubuntu.com) edgy-backports/multiverse Sources
Get:8 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Translation-en_US
Get:9 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/main Translation-en_US                      
Get:10 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Translation-en_US     
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/main Translation-en_US                        
Get:11 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/multiverse Translation-en_US     
Get:12 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/restricted Translation-en_US               
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/multiverse Translation-en_US        
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/restricted Translation-en_US                  
Get:13 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Translation-en_US       
Get:14 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/multiverse Translation-en_US               
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/multiverse Translation-en_US                  
Get:15 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Translation-en_US     
Get:16 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/universe Translation-en_US                 
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/universe Translation-en_US
Get:17 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Translation-en_US
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates Release.gpg
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Translation-en_US
Get:18 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:19 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:20 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/main Translation-en_US
Get:21 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security Release [50.9kB]
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/main Translation-en_US
Get:22 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/universe Translation-en_US            
Get:23 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US       
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Packages                       
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Packages                 
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US          
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/multiverse Packages                 
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed Release.gpg                          
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Sources                        
Get:24 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US      
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Sources                  
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US         
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/multiverse Sources                  
Get:25 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/main Translation-en_US            
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Packages                   
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Sources                    
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/main Translation-en_US               
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Packages                 
Get:26 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/universe Translation-en_US        
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Packages                       
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Packages                   
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/universe Translation-en_US           
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/restricted Sources                  
Get:27 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US      
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/main Sources                        
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) edgy-security/universe Sources                    
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US         
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports Release.gpg                         
Get:28 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:29 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/main Translation-en_US
Get:30 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Get:31 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Ign [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:32 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy Release [34.7kB]
Get:33 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates Release [38.4kB]                   
Get:34 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed Release [38.4kB]                  
Get:35 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports Release [44.6kB]                 
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/main Packages                                 
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/restricted Packages                           
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/multiverse Packages                           
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/universe Packages                             
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/restricted Sources                            
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/main Sources                                  
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/multiverse Sources                            
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy/universe Sources                              
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/restricted Packages                   
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/main Packages                         
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/universe Packages                     
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/main Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/universe Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/main Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/restricted Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/main Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/universe Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-proposed/multiverse Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/main Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/universe Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/main Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/universe Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 252kB in 1m19s (3176B/s)
Reading package lists... Done


---

### Post by Kateikyoushi on 2007-03-12
It is perfect.

---

### Post by manic34 on 2007-03-12
I am eternally in your debt

Thankyou
Thankyou
Thankyou

---

