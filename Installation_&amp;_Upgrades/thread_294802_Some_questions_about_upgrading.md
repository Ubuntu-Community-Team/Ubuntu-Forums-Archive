---
title: "Some questions about upgrading"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by Biffy on 2006-11-07
So i've been reading some about upgrading from Dapper to Edgy and that there's been some problems. I've got my Dapper install and i am very pleased with it. 

So i've decided to wait to upgrade to Edgy. But my question is, when Feisty is released (and im still running Dapper) what will happen when i run upgrade-manager -c ? Will it then upgrade from Dapper to Feisty and everything will break OR will it do it the right way so my system wont break? How does upgrade-manager behave when doing this? Maybe upgrade-manager will understand that im running Dapper and hence upgrade to Edgy and from there upgrade to Feisty? Im kinda curious here. :)

---

### Post by Kateikyoushi on 2006-11-07
You have to upgrade to edgy first before upgrading to feisty.

> Try to upgrade from immediately previous versions, e.g. Dapper to Edgy not Breezy to Edgy. If you are running Hoary for instance, upgrade Hoary->Breezy->Dapper->Edgy. [LINK]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Upgrading_Ubuntu")

---

### Post by Biffy on 2006-11-07
Ok, thanks for replying.

But, will update-manager understand this? Or do i have to do a dist-upgrade the old fashioned way, by editing my sources run a apt-get dist-upgrade ?

---

### Post by Biffy on 2006-11-07
Can someone please answer to this? I need to know if i must upgrade to edgy (with update-manager) within theese 6 months or if i just can relax, wait for Fiesty and let update-manager do the thinking for me.

---

### Post by Biffy on 2006-11-07
Maybe you dont understand cause of my bad english. :)  Im gonna try to make myself as clear as possible.

If i continue to run Dapper until Feisty is released, i will need to upgrade to Edgy first. This is clear, but when doing this, should i use dist-upgrade or update-manager? Since i've been reading that update-manager is the official way to upgrade in Ubuntu nowadays, im not really sure wich method to use. Im unsure if update-manager will try to install feisty directly, and hence crash my Ubuntu installation.

---

### Post by Kateikyoushi on 2006-11-07
I saw today someone mentioning that he always updated the old fashioned way but now for edgy used the update manager which borked things. I would say when the next version comes out see the first update results and decide which way to update.

---

### Post by DonKyot on 2006-11-07
> **Biffy said:**
> Maybe you dont understand cause of my bad english. :)  Im gonna try to make myself as clear as possible.

If i continue to run Dapper until Feisty is released, i will need to upgrade to Edgy first. This is clear, but when doing this, should i use dist-upgrade or update-manager? Since i've been reading that update-manager is the official way to upgrade in Ubuntu nowadays, im not really sure wich method to use. Im unsure if update-manager will try to install feisty directly, and hence crash my Ubuntu installation.
i'm still new to ubuntu etc. but as far as I can see, the update manager uses the sources (defined, for example by System>Admin>Software Sources - or apt/sources.list?) which define which dist you're updateing from.
No?

---

### Post by Biffy on 2006-11-08
> **Kateikyoushi said:**
> I saw today someone mentioning that he always updated the old fashioned way but now for edgy used the update manager which borked things. I would say when the next version comes out see the first update results and decide which way to update.


Yes, but is update-manager even capable of updating from Dapper  to Feisty? You are saying that i must install Edgy before going to feisty. But when Feisty is released, i guess update-manager wants to upgrade to the latest Ubuntu version, feisty that is.

Im trying to ask how update-manager behaves when upgrading from Dapper to Feisty. I need to know if i must run update-manager within theese six months and i must know if im screwed when Feisty is released if i havent upgraded to Edgy yet.

---

### Post by Biffy on 2006-11-08
> **DonKyot said:**
> i'm still new to ubuntu etc. but as far as I can see, the update manager uses the sources (defined, for example by System>Admin>Software Sources - or apt/sources.list?) which define which dist you're updateing from.
No?


So you are saying that update-manager understands wich Ubuntu version im using and then upgrades to the NEXT version. 

Like if Feisty is released and im running Dapper. When running update-manager it understands that im using Dapper and then installs Edgy for me and then installs feisty?

---

### Post by Biffy on 2006-11-08
Some people are saying that Dapper is LTS and that upgrade to Edgy not is recomended. Let's just hope that there will be an easy and safe way to upgrade from Dapper to Feisty when it has been released. And since update-manager is the official way, lets just hope it works.

---

### Post by Kateikyoushi on 2006-11-08
But Feisty won't be an LTS either why do you want to upgrade to it and not edgy ? Probably by the time the next LTS is about to released we have a way to upgrade driectly from LTS to LTS.

---

### Post by Biffy on 2006-11-09
> **Kateikyoushi said:**
> But Feisty won't be an LTS either why do you want to upgrade to it and not edgy ? Probably by the time the next LTS is about to released we have a way to upgrade driectly from LTS to LTS.

Ok, i tought Feisty would be the next LTS. Sorry.

But still, i have not gotten an answer regarding updating from Dapper to Feisty. You are saying that i must upgrade Dapper-Edgy-Feisty , but how? By manually editing my sources (the non-official way) OR will update- manager do all the work for me by first upgrading to Edgy and then to Feisty? I need to know how update-manager works in this matter.

---

