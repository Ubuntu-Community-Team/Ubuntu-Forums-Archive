---
title: "Can't upgrade from 10.10 to 11.04"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by GammaPoint on 2011-10-04
I'm currently running Ubuntu 10.10 and trying to upgrade to 11.04 (in preparation to upgrade to Ocelot later). But when I click on the upgrade link in Update Manager it tells me "Could not download the release notes: Please check your internet connection", even though I'm clearly connected to the internet. 

Any idea what the problem could be?

---

### Post by dino99 on 2011-10-05
do it with synaptic (select higher release)

---

### Post by GammaPoint on 2011-10-05
> **dino99 said:**
> do it with synaptic (select higher release)

Thanks for the suggestion. I opened Synaptic package manager but am not sure how to find "higher release". Do I need to search for something in particular or where should it be? Thanks!

---

### Post by GammaPoint on 2011-10-10
Anyone else have any suggestions? I still am not able to upgrade.... :(

---

### Post by thatguruguy on 2011-10-10
First of all, make sure you're completely updated in 10.10.

Secondly, go into Software Sources and make sure "backports" isn't enabled.

Run the following from a terminal, and feel free to post the results here if it doesn't work:
```
sudo apt-get install update-manager-core

Then you'll need to edit your /etc/update-manager/release-upgrades
[CODE]gksu gedit /etc/update-manager/release-upgrades
```
... and make sure you set the following line in that file:
```
Prompt=normal
```
Save the file, and then run the following in the terminal:
```
sudo do-release-upgrade
```

---

### Post by GammaPoint on 2011-10-10
Thanks for the response. I can't sudo apt-get install update-manager core. If I try I get the following error:


```
$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpango1.0-0 : Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu5.1 is to be installed
E: Broken packages
```

Perhaps this is due to something I tried before you posted. Following a solution that others have posted in the past for other upgrades, I tried to do:

```
sudo sed -i 's/maverick/natty/' /etc/apt/sources.list

```

When I do this, and  then open update manager, it tells me "Not all updates can be installed, run a partial upgrade, to install as many updates as possible". Is there a way to reset my behavior to the situation that I was in before I input that command, or should I go ahead with this partial upgrade deal I've forced upon myself?

Thanks!

---

### Post by saenger on 2011-10-10
> **thatguruguy said:**
> First of all, make sure you're completely updated in 10.10.

Secondly, go into Software Sources and make sure "backports" isn't enabled.

Run the following from a terminal, and feel free to post the results here if it doesn't work:
```
sudo apt-get install update-manager-core

Then you'll need to edit your /etc/update-manager/release-upgrades
[CODE]gksu gedit /etc/update-manager/release-upgrades
```... and make sure you set the following line in that file:
```
Prompt=normal
```Save the file, and then run the following in the terminal:
```
sudo do-release-upgrade
```

I'll piggy-back on this thread.

I want to upgrade from 8.04.  When I carry out the suggestions given here, I get the following message:  "Checking for a new ubuntu release
No new release found"

Any suggestions?

---

