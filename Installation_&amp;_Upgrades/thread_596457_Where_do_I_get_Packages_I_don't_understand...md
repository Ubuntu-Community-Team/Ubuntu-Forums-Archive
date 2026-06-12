---
title: "Where do I get Packages?? I don't understand.."
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by mason01 on 2007-10-29
Hi, I'm new with Ubuntu. I hope this is posted in the right place.

 I have Ubuntu 7.04 installed and working. Now I'm trying to install MySQL. I have the understanding that I should be able to do this through the "Synaptic Package Manager" - I guess it should be "added" to "Third-Party Software", and then the installation should all be really simple? However, I can't figure out where the MySQL "Package" is supposed to come from in the first place (I'm also going to have to install Apache2, Python, Mod_python, subversion ...). 

Everyone says how easy this should be, but I'm starting to sweat bullets. I've Googled around for hours to no avail. I see a lot of this sort of thing:

"Installing Mysql database in Ubuntu
#apt-get install mysql-server mysql-client libmysqlclient12-dev"

"12 MySQL
In order to install MySQL, we run
apt-get install mysql-server mysql-client libmysqlclient15-dev"

... like it should be a piece of cake.

I'm thoroughly confused. There never seems to be any mention of where the Package comes from (I have everything selected under Software Sources-->Ubuntu Software).

I just can't imagine that I should be finding it this difficult. Can anyone out there enlighten me?

mason

---

### Post by forestpixie on 2007-10-29
so what have you actually done to try and install it?

---

### Post by mason01 on 2007-10-30
I've gone two routes to try to install it: 

1, Synaptic Package Manager , 
     Settings-->Repositories
                              -->Software Sources:
                                    ->selected everything but "source code"
                                    ->"Download from" is set to "Custom servers"
                              -->Third-Party Software:
                                    ->Added "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free"
     Closed the Settings window, then clicked "Reload"

2. From the Terminal, I followed an example from "http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories" :
     -->sudo gedit sources.list
          -->Found the following sources:
               deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty restricted main
               deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates restricted main
               deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
               deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main
               deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
               deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multivers
          -->Then I uncommented out:
               deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe       multiverse
               deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
          -->Next, I added the one Package source I could find:
                deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
     -->After that I *tried* to download any needed gpg keys and add them to the keylist using:
         "apt$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -"
          This resulting in the following:
           "gpg: no valid OpenPGP data found", but I still think the Package is okay.
     -->Finally, I ran:
           "sudo apt-get update && apt-get upgrade", which seemed to work.
    
Anyway, with the exception of the "keylist" not working out, everything seemed to go just fine, but when I search for MySQL in Synaptic I don't get any results, so I don't have anything to mark for installation. 

My problem (as far as I can see) is that I don't know what repositories to add to get MySQL ( or Apache, or Django, or Subversion).

How am I doing? Am I close? Will anyone help me out?

Thanks,

mason.

---

### Post by mason01 on 2007-10-30
Just to follow up, I'm not sure why, but as it turns out, rebooting fixed everything, and the MySQL package loaded the application successfully.

mason

---

### Post by zvacet on 2007-10-30
Maybe you are interested in **LAMP**,and if you do you can install it very simply by going to **synaptic>edit>mark packages by task**.

---

