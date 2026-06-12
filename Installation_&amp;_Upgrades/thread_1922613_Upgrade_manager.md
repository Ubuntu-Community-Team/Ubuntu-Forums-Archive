---
title: "Upgrade manager"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by nickeys1 on 2012-02-09
Upgrade manager won't work it keeps saying "check internet connection". Can anyone help please?

---

### Post by jerrrys on 2012-02-09
Open a terminal and enter:

sudo apt-get update

Get any errors?

---

### Post by nickeys1 on 2012-02-09
Thanks for replying. Did as you asked and this is what i get:-

W: Failed to fetch [http://ppa.launchpad.net/unity/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/unity/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by raja.genupula on 2012-02-09
open your update manager -> settings from 1st tab at download from change your server to main server or best server from your location . 

and then try again .

---

### Post by jerrrys on 2012-02-09
And if Raja's suggestion does not work, try this:

Open a terminal and enter:

gksudo gedit /etc/apt/sources.list

Then navigate to line:

 [http://ppa.launchpad.net/unity/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/unity/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)
 
 And comment (#) that line out. So it looks like this:
 
 #[http://ppa.launchpad.net/unity/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/unity/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)
 
 And save.  Update Manager should now work.

By adding a # to this line, you have deactivated it.

Edit: sudo replaced with gksudo to make nerdy types happy :)

---

### Post by MG&amp;TL on 2012-02-09
Hate to be a nerd :P , but that should probably be:

```
gksu gedit /etc/apt/source.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Just a recommendation. :)

---

### Post by Cavsfan on 2012-02-09
I just clicked on your link and it gave me 404 Not Found. It may be that is temporarily unavailable. 
I get that once in a while. If it is a known good software source, you should just wait a while.

I was told not to use update manager by **ranch hand **(who is a very knowledgeable user on here) and to use command line.
He calls it Update Mangler! 
I always use: 
```
sudo apt-get update 
sudo apt-get upgrade
```It will show you if anything is being help back like a kernel.

Then after I update I use this to get the kernel that is being held back:

```
sudo apt-get update 
sudo apt-get dist-upgrade
```Just thought I would provide another thought/approach.

---

### Post by jerrrys on 2012-02-09
@Cavsfan:

Update Mangler; thats cute.  Leave it to ranch hand to tell it like it is.

Want to do it right?  download Synaptic Package Manager (a GUI for apt-get)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

To download, open a terminal and enter:

sudo apt-get install synaptic

And you nerdy types :P I edited my post.

---

### Post by Cavsfan on 2012-02-09
**jerrrys**, I just like the CLI way. Someone some where (in this forum) showed me how to create a script to do it.

I just type "ud" (what I named the script) along with my password and it executes 
**sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean**
and "ud2" executes
**sudo apt-get dist-upgrade**

Some times my conky will start up too fast and be on top of everything and I have to enter in a terminal **killall conky** and then
look up in my Startup Applications the command to start conky and conkyrythymbox back up.

I keep forgetting I set that up as a script too and could just be entering "rc1" and "rc2".
The mind does strange things from time to time. Especially with the medication I am on.

---

### Post by Cavsfan on 2012-02-09
While we're on the subject of making this easy, here is how to make the update a script like mine is:

Open a terminal and enter **gksudo gedit ~/.bashrc**
Then towards the bottom of that file you will see aliases.

I put mine just above this line **# Alias definitions.**

I put this:
```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```

Then once you save the file, you can just enter "ud" and ud2".
And of course you can put anything else you want to automate there too if there are any command lines you use frequently.

---

