---
title: "Upgrading Ubuntu Hardy [8.04] to something more modern ... in 2016... with EOL here"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by anon_m on 2016-01-26
So this is going to sound weird. I have a Hardy 8.04 VM for a class that I am taking. It's purposely out of date because it's one of two insecure VMs that we need to secure. Obviously the first step in securing this VM is upgrading to something more modern.

I do not have access / permissions to do a clean install. By clean install, I cannot just reinstall a new operating system over the VM. I can only upgrade Hardy.

I first tried this page: [https://help.ubuntu.com/community/EOLUpgrades/Hardy](https://help.ubuntu.com/community/EOLUpgrades/Hardy)

On this page I edited sources.list, went ahead and ran update and safe-upgrade. What was weird was it prompt the removal of 201 user programs (gedit, nano, etc etc) and then performing a sudo do-release-upgrade gave a command not found. After this I reverted back a snapshot.

Second thing I tried was the alternate CD install. I tried three different CDs (updating in steps?) 9.04, 8.10, and 9.10. I was able to mount the disk successfully, but running the upgrade file gave me an error (A Python import error?) that said there is no module named apt. Doing some research, I found that I needed the python-apt package. Doing a dpkg -l command, it says that I do have the package (0.7.94.2ubuntu6) so at this point I'm at a loss.

What did I miss here and is this a lost cause or doable?

---

### Post by grahammechanical on 2016-01-26
I am not sure from your description if Ubuntu 8.04 is the host OS or the guest OS in the VM.

If 8.04 is the guest OS, then the most obvious way to secure 8.04 would be to delete the VM. Did you read the foundation wiki page for End of Life upgrades?

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

It says something different from the instructions in the link that you provided.

> **Update sources.list**

 To begin the upgrade, make sure you have a sources.list like the following, with CODENAME being your release, e.g. quantal. 

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multiverseYou can use -backports and or -proposed if you want. For more information about repositories see [this page]("https://help.ubuntu.com/community/Repositories/Ubuntu").

You need to change the URLs in the sources list from whatever archive.ubuntu.com they are set for to old-releases.ubuntu.com. Then you need to update & upgrade 8.04

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Notice, we use apt-get not aptitude. Aptitude is not installed by default. Certainly not in newer versions of Ubuntu. Installing update-manager-core & update-manager applies more to server systems than to desktop systems. You may find that those two packages are installed by default on desktop systems.

```
sudo do-release-upgrade
```

And then you do it all again once you get to 10.04 because 10.04 is out of life and you need to move on the 12.04 which will reach end of life itself April next year. It will be an educational experience but not  a practical way of doing things. And I have done it as an experiment. Only I did not go from LTS to LTS but through all the releases until the desktop became corrupted going from 10.10 to 11.04. It was an end of life upgrade too far.

Regards.

---

### Post by matt_symes on 2016-01-26
Hi

I'm having a crack at this myself, in a KVM VM.

Hardy 32bit.

Currently in the process of upgrading to Lucid.

I'll let you know how it goes and what problems i see.

Kind regards

---

### Post by anon_m on 2016-01-26
Thanks for also trying this. Let me know if you get success.

I was able to upgrade from 8.04 to 10.04 by installing the following packages manually (using dpkg -i):

python-apt_0.7.4
python-gnupginterface_0.3.2-9
python-vte_0.16.13-1
update-manager-core_0.87.31
update-manager_0.87.31

Then I downloaded the 10.04 alternate CD ISO and I was then able to run the installer file.

However, when booting up the new upgrade, my keyboard doesn't work. Because of this, I can't login which means I can't access a web browser to download the next ISO. I'm able to SSH into the machine but no luck into really getting any upgrade going. I can't even install wget...

I wish that I could say that grahammechanical's post was helpful, but it wasn't. Changing the source list (to precise code name) still gives 404's when doing an apt-get update. The dist-upgrade command doesn't even exist for me either..

---

### Post by matt_symes on 2016-01-27
Hi

I managed to upgrade from 8.04 to 14.04 in KVM using virt-manager but it was not an easy process.

I had to use the cirrus graphics card for 8.04 as i could not get it to work with an other emulated card. In the 14.04 card, i had to replace it with another (all others worked) to get to a desktop.

Another thing, to update to 10.04, i used the old sed trick to upgrade using the old-release.ubuntu.com repository. 

This worked but the update from 10.04 to 12.04 required that i had to run an unauthenticated upgrade ! This'll fail your test :) I suspect there's a way around this and i'm going to try to work out how to do it in another run.

After that, it was plain sailing up to 14.04 when i had to change fro the cirrus graphics card.

All in all, it took just over 6 hours to complete (but my host VM machine is running the powersave governor).

What virtualisation software are you using ?

If i can't find out how to get around the unauthenticated upgrade from 10.04 to 12.04 then this is not even an option for you. 

If you're interested, i can give you the specs of the guest VM machine.

Kind regards

---

### Post by ronny13 on 2016-02-26
> [COLOR=#000000]Another thing, to update to 10.04, i used the old sed trick to upgrade using the old-release.ubuntu.com repository. [/COLOR]

How did you do this? I'm trying to update 08.04 but the Update Manager is trying to get me to go directly to 12.04.

---

