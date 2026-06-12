---
title: "Upgrading from 6.06 to 6.10?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Jonas_Henricsson on 2007-04-21
I want to upgrade from Dapper Drake 6.06 to 6.10. I found this guide: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

It says that update manager is supposed to do the trick: "If you have a working network connection, it should then inform you about a new release and offer to upgrade your system."

Well, I have a working connection, but my update manager says nothing about a new version. What can I do about this? I'll be most thankful for any help.

/Jonas

---

### Post by jpeddicord on 2007-04-22
I do believe Dapper has disabled the update because it is an LTS version. To get the update to Edgy, open a terminal and type this:```
sudo update-manager -c
```
Update Manager will run again, but this time at the top of the window it will tell you about a new distribution release that is available.

If you want to upgrade to Feisty after upgrading to Edgy, Update Manager will automatically notify you. (Be advised however that you can not upgrade directly from Dapper to Feisty though. You need to upgrade to Edgy first.)

Jacob

---

### Post by Jonas_Henricsson on 2007-04-23
Yeah, I managed. Thanks!

But it seems like I have the same problem as many others, Feisty does not appear either. People are saying that the problem is solved by downgrading update manager to 0.45.2. But I can't even upgrade it to 0.45.3. So I got 0.45.2 and I still can't see Feisty.

Does that mean my repositories are inadequate?

/Jonas

---

### Post by zvacet on 2007-04-23
If you have all repositories open 

```
sudo aptitude update && sudo aptitude upgrade
```

After this you have to be able to see massage for upgrade to Feisty in update manager.

---

### Post by Jonas_Henricsson on 2007-04-23
Thanks, man, think I'm getting somewhere. Still not there though.

This is really weird. When I run update manager, it finds a new distribution version. However, when I start it, it says it's upgrading to 6.10. Maybe my upgrade wasn't complete. In my system info it says that I have 6.10...
I say yes to upgrade and get an error message, saying that the following packages couldn't be authorized (authentisized? got local language... =(...)  :

gaim
gaim-data
gaim-dev
libtwolame0
mencoder
python-musicbrainz



One question: how do I know if I have all repositories open? I copied the ones in the upgrade instruction.

Thanks again for your help!

---

### Post by zvacet on 2007-04-23
Try first 
```
lsb_release -a
```

that will tell you wich version you are runing.You can also see in system>about Ubuntu

This i how to add repositories


[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

And you sed that is upgraded to 6.10.if this is true make your Edgy up-to-date and after that you can upgrade to Feisty.

If you are upgraded to Edgy you have to change your source list,and do it like this
```
  sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

---

### Post by Jonas_Henricsson on 2007-04-24
lsb_release -a

gives that I have 6.10.

I've tried the repositories here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories#How_to_apt-get_the_easy_way_.28Synaptic.29)

and those from: [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Still I get the same error. Any more ideas? If you need more info, ask!

Thanks again!

---

