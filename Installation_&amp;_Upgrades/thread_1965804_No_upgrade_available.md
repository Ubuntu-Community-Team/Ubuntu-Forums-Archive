---
title: "No upgrade available?"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by smiggy on 2012-04-26
Wotcha peeps,

On 11.10
Just done the following:-

#sudo apt-get update
#update-manager -d -c
No upgrade?

#sudo do-release-upgrade -d
No new release found?

What gives???

:(

---

### Post by Cavsfan on 2012-04-26
> **smiggy said:**
> Wotcha peeps,

On 11.10
Just done the following:-

#sudo apt-get update
#update-manager -d -c
No upgrade?

#sudo do-release-upgrade -d
No new release found?

What gives???

:(

I would advise on backing everything important up and doing a clean install. If not there will be a lot of stuff left from 11.10.
I did an upgrade one time and everything went well for a while but, I ended up needing to do a clean install any way. JMO

---

### Post by azcv on 2012-04-26
I am with ubuntu 12.04 lts beta.I want to upgrade to the final release,but update manager says that my system is up to date.I think that i have to wait for 1-2 days.
Is it even possible to upgrade from beta to final or i will have to make a clean install?Is there an option to save apps and settings over the new install?:confused:

---

### Post by jadtech on 2012-04-26
the up grade is available I got it about 1am this morning 
try this in the terminal .

 sudo apt-get dist-upgrade

---

### Post by Cavsfan on 2012-04-26
> **azcv said:**
> I am with ubuntu 12.04 lts beta.I want to upgrade to the final release,but update manager says that my system is up to date.I think that i have to wait for 1-2 days.
Is it even possible to upgrade from beta to final or i will have to make a clean install?Is there an option to save apps and settings over the new install?:confused:

If you have been keeping up with updates, your system should be up to date. You could wait until 12.04.1 comes out and then do 
a clean install.

As far as backing up, I just use my 1TB USB drive to copying what I want to keep then do a clean install.

**jadtech**, you should precede that withe sudo apt-get update first.

```
sudo apt-get update 
sudo apt-get upgrade
``````
sudo apt-get update
sudo apt-get dist-upgrade 
```

---

### Post by azcv on 2012-04-26
> **jadtech said:**
> the up grade is available I got it about 1am this morning 
try this in the terminal .

 sudo apt-get dist-upgrade

There is no upgrade for me.Maybe i have to wait?Or maybe the problem is tham I am on a 12.04 beta?I don't know.I will wait for a few days and if there is no ugrade i will make a clean install.

---

### Post by Cavsfan on 2012-04-26
This is much better than using Update Manager!
```
sudo apt-get update  
sudo apt-get upgrade 
``````
sudo apt-get update 
sudo apt-get dist-upgrade
```I cannot even get the Firefox update right now, servers too busy I believe. I'm just going to wait.

---

### Post by jerrrys on 2012-04-26
> **smiggy said:**
> Wotcha peeps,

On 11.10
Just done the following:-

#sudo do-release-upgrade -d
No new release found?

What gives???

-d, --devel-release
              Check if upgrading to the latest developmental release is possible

> **jadtech said:**
> the up grade is available I got it about 1am this morning 
try this in the terminal .

 sudo apt-get dist-upgrade

dist-upgrade is not the same

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dist+upgrade&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dist+upgrade&sa=Search&cof=FORID:9)

The command is:

sudo do-release-upgrade

---

### Post by azcv on 2012-04-26
There is no new version with all the commands.

---

### Post by jadtech on 2012-04-26
i was on 12.04 beta here just do all the updates that pop up and you will have the new release ..

---

### Post by azcv on 2012-04-26
> **jadtech said:**
> i was on 12.04 beta here just do all the updates that pop up and you will have the new release ..

Hm.But my kernel is 3.2.0-23 and in the changelog of 12.04 final the kernel version is 3.2.14?

---

### Post by smiggy on 2012-04-26
Upgrade option now available, guess was just due to load on servers and/or lag.

Thanks all!

;)

---

### Post by jadtech on 2012-04-26
> **azcv said:**
> Hm.But my kernel is 3.2.0-23 and in the changelog of 12.04 final the kernel version is 3.2.14?

yup the update I got last night just doing normal update new kernel and so far more then a dozzen other updates

---

### Post by azcv on 2012-04-26
> **jadtech said:**
> yup the update I got last night just doing normal update new kernel and so far more then a dozzen other updates

I guess i have to wait.I have updaded 12.04 beta regularely and i don't think i 'll get a lot of updates.But i want the new kernel.

---

### Post by jadtech on 2012-04-26
well all was there about  roughly 12;30 EST though at the time I had changed the manager to US servers pretty sure they all cant or dont get new stuff at the same time ..

---

### Post by azcv on 2012-04-26
> **jadtech said:**
> well all was there about  roughly 12;30 EST though at the time I had changed the manager to US servers pretty sure they all cant or dont get new stuff at the same time ..

The Greece server gives me 3.2.0-24 kernel.

---

### Post by jadtech on 2012-04-26
thats it :)

---

### Post by jadtech on 2012-04-26
after you do that and reboot over the next day many more updates will come

---

### Post by pchokola on 2012-04-26
I am also getting a "No new release found" when I issue the "do-release-upgrade" command trying to upgrade from 10.04 LTS to 12.04 LTS.

I followed the release notes update instructions exactly:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer#From_10.04_to_12.04](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer#From_10.04_to_12.04)

Am I under the impression from reading this thread that it is just a matter of overloaded servers on Ubuntu's side?

---

### Post by jadtech on 2012-04-26
pretty much that is  what it is and the upgrade takes about an hour and half or most in down load and another near 2 hours install so each one upgrading is  keeping things tide up a while .. 

my recommendation has been to change server where you are getting up grade this seems to be working  to a degree ..

thing is you should at the least get the upgrade to 11.04 or 10 avalable   though I would think ..

---

### Post by pchokola on 2012-04-26
> **jadtech said:**
> pretty much that is  what it is and the upgrade takes about an hour and half or most in down load and another near 2 hours install so each one upgrading is  keeping things tide up a while .. 

my recommendation has been to change server where you are getting up grade this seems to be working  to a degree ..

thing is you should at the least get the upgrade to 11.04 or 10 avalable   though I would think ..

Thanks.  Will try again in a day or two.

---

### Post by pchokola on 2012-04-26
> **pchokola said:**
> Thanks.  Will try again in a day or two.

Here is an interesting post to a thread I found regarding the same problem.  I am a bit reluctant to try this however, until it is verified from other sources:

" (This is an incomplete answer and needs improvement and testing):
  From talking to some developers in IRC it seems that 10.04 to 12.04  upgrades don't get turned on until the point release, 12.04.1. 
  You need to a do-release-upgrade -d or update-manager -d to upgrade from vanilla 10.04 to 12.04, this will "trick" the upgrader  to give you 12.04. "

---

### Post by pchokola on 2012-04-26
> **pchokola said:**
> Here is an interesting post to a thread I found regarding the same problem.  I am a bit reluctant to try this however, until it is verified from other sources:

" (This is an incomplete answer and needs improvement and testing):
  From talking to some developers in IRC it seems that 10.04 to 12.04  upgrades don't get turned on until the point release, 12.04.1. 
  You need to a do-release-upgrade -d or update-manager -d to upgrade from vanilla 10.04 to 12.04, this will "trick" the upgrader  to give you 12.04. "


SOLVED ! (AT LEAST MY PROBLEM, NOT NECESSARILY THE ORIGINAL POSTER)  I was reading through the "Ask Ubuntu" page and discovered that someone was able to get the upgrade to work following the same instructions that I used.  Well I checked the page and they changed the instructions since this morning!!!!  They changed "do-release-upgrade" to "do-release- upgrade -d".  The old page was up on a different computer so I know for a fact that they changed the instructions.  Note the addition of the -d.  Now everything works.

---

