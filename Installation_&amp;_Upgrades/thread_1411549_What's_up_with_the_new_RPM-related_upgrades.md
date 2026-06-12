---
title: "What's up with the new RPM-related upgrades?"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by priegog on 2010-02-20
Pretty much self explanatory:
This morning I went into the update manager, and found a bunch of RPM package-management stuff such as rpm, alien, compiling tools, etc. What is up with this?
I suspect they are setting the scenery for some big press release saying they now support RPM packages in Ubuntu too. 
Any ideas? (or better, inside info from someone who knows)

Edit: there are also some email packages... What is going on?

---

### Post by tommcd on 2010-02-20
I have never had any RPM upgrades, or RPM anything in Ubuntu.

Big fat important question here:
Have you added any third party repositories, like the ppa repositories, or any other repositories that were not present in a default Ubuntu install, to your /etc/apt/sources.list, or to your /etc/apt/sources.list.d directory ?

---

### Post by priegog on 2010-02-20
Yeah, only the google repos, but I doubt they have anything to do with this. Also, they came under the "distribution updates" subtitle, so this further makes me wonder. Also, this happened to 2 different computers (different owners even).
But meh, I guess it doesn't really matter. I was just really curious, that's all.

---

### Post by tommcd on 2010-02-20
What google repos do have? The reason I ask is because ...

A while back I installed the linux version of google chrome from the .deb file listed on the google chrome web site. So Google (the company that has as it's mantra "Don't be evil", decided to add the google-chrome repo to my /etc/apt/sources.list.d directory without even asking or telling me that it was doing this. 

Recently I ran 'apt-get update', and lo and behold, the most recent upgrade to google-chrome wanted to install 41 NEW packages that I was not familiar with. So I said NO!! I am always cautious when I see stuff like that.
I will not use google chrome anymore.
 Even in Slackware, which does not manage dependencies at all, they somehow manage to install updates every time you launch chrome. Nothing else in Slackware behaves like this. This is 100% contrary to the Slackware way of doing things.
I do not trust google chrome with controlling my system. I can live without it.

---

