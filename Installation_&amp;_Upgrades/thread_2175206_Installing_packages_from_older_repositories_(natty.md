---
title: "Installing packages from older repositories (natty/raring)"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by HenrikJay on 2013-09-18
In case this has been answered I apologize, could not find anything on it.

Summary:
System is 13.04 (raring).
Have a private (PPA) repository that I want to add applications from.
The repository only have dist folders for up to 11.04 (natty).
I have added the repository as "deb [http://.](http://.)... natty main" but it still doesn't show up in list of available sources (have tried adding manually and as PPA/key).

When running "sudo apt-update) I can see that it is getting a hit on the repository.

Question:
Is it possible to set raring to install apps from a repository and choose the apps under the natty dist?

/HenrikJay

---

### Post by deadflowr on 2013-09-18
If running raring, it is best to run raring packages.
Natty is old and quite dead.
Quite a few packages for natty are likely incompatible with what is offered in raring.
Mixing the two is going to cause you nothing but heart ache and hair loss.

---

### Post by HenrikJay on 2013-09-18
Fully aware of incompatibility risks and not relevant in this case.

What I need to know if it is possible or not and how.

---

### Post by oldos2er on 2013-09-18
It's certainly possible, but it's also possible it might cause problems with your system. Can you contact the owner of the PPA to see if they have any other updates available?

Rather than adding an old PPA, I'd try downloading the package(s) you want and installing it manually. Your choice.

---

### Post by HenrikJay on 2013-09-18
So it is possible, yet the source does not show up in the list of sources when browsing by Origin in Synaptic.
Am I missing something?

As mentioned before:
URL is good, apt-get update can contact the source and successfully download package list.
It shows up as a repository in synaptic under Other Software.
It successfully created a list file under apt/sources.list.d

It does not show up in synaptic.
I can't install packages I know is in the repository using apt-get install


So, if not focusing on using older repositories, how do I add a repository that is for natty to a Raring dist?
Is there anything else that is needed then just adding the repository and changing dist to natty in the sources.list file?

Thanks.

---

### Post by deadflowr on 2013-09-18
I already stated that natty is dead.
The repos are gone and moved to repo afterlife.
[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions](http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions)

Beyond that the advice on trying to find the individual packages you want is a better alternative than trying to get repositories working, which may or may not cause serious problems down the road.
A lot has changed between natty and raring.
It's quite possible that the needed libraries/other dependencies are uninstallable.

---

### Post by HenrikJay on 2013-09-18
Guys, I understand your comments about old packages/repositories and new dist but you are not answering the question, you are providing opinions (not trying to be rude, just trying to get answer to the question).

This is not for the official repos that are dead, as mentioned initially "[COLOR=#000000]Have a private (PPA) repository that I want to add applications from.[/COLOR]". Meaning this repo has packages for natty on it.

The question if adding a old repo to a new dist can be done was answered by oldos2er stating it is possible but as I commented I have not gotten it to work by adding it as a normal repo. Meaning do you have to do something special to add it to synaptics.

---

### Post by deadflowr on 2013-09-18
PPAs die, just like the normal repos do.
Have you run 
```
sudo apt-get update
```
from a terminal after trying to add the ppa to your sources.list(d)
And if so, does it show up listed?
Or does it bring up a 404.

---

### Post by HenrikJay on 2013-09-23
Sorry for late response, been traveling.
Yes PPA's die but as I have mentioned, this is still there and no, don't get 404 on the location, it is still there.

---

