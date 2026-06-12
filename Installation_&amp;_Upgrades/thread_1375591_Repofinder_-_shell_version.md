---
title: "Repofinder - shell version"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by ingalex on 2010-01-08
I am pleased to announce that the shell version of [Repofinder]("http://www.sourceslist.eu/installare-software-tramite-repository/repofinder-versione-per-terminale/") for Karmic Koala Ubuntu 9.10 is ready. But what is it? For some time there is a web version of Repofinder. The Repofinder is a search engine which aims to find the repository containing certain packages you want to install. In this way you can avoid insert or activate a repository in your sources.list reckless. So the [Repofinder]("http://www.sourceslist.eu/installare-software-tramite-repository/repofinder-versione-per-terminale/") allows us to add to our sources.list the right repository at the right time.
It 'important to be very cautious in adding the unofficial repository because it can endanger the stability of your distribution.
Would be desirable to disable (comment) non official repository present in sources.list after install / upgrade some packages.
To install the repofinder you just add the following repository to your sources.list:
```
deb http://www.sourceslist.eu/repo/ubuntu karmic main non-free
```
running from a terminal the following line of code:
```
echo "deb http://www.sourceslist.eu/repo/ubuntu karmic main non-free" | sudo tee -a /etc/apt/sources.list
```
You must add the repository's public key by running:
```
sudo gpg --keyserver hkp://pgp.mit.edu --recv-keys FA088BA5 && sudo gpg --armor --export FA088BA5 | sudo apt-key add -
```
Then install the package by running:
```
sudo apt-get update && sudo apt-get install repofinder
```
To search the repository containing the package simply run:
```
repofinder <package_name>
```
To invoke the help you simply run:
```
repofinder -h
```
or 
```
repofinder --help
```
To give you an idea on the functioning of [Repofinder]("http://www.sourceslist.eu/installare-software-tramite-repository/repofinder-versione-per-terminale/"), you can look at the following animated gif:
[IMG]http://www.sourceslist.eu/wp-content/uploads/2009/12/repofinder.gif[/IMG]
Obviously this is only a first version of the script so please report bugs and problems so that I can try to solve them.
Later I plan to implement the ability to search the repository not only by the name of the package, but also by the version.
Also, always with the special collaboration of M4iden_Rul3z, we are trying to develop a version of Repofinder allowing you to search through a graphic interface made with PyQt. Moreover, this version of Repofinder will be granted a set of advanced features for managing the repository.
I would be grateful if you could give me some reviews or constructive criticism on this script and possibly even give me advice on how to improve it.
I sincerely hope that this script can be useful.
Bye Ingalex

---

### Post by HappySmack on 2010-01-10
Does this work on 64-bit version?

EDIT: Found it on the site.

Does this provide the keys, or any anticipation of such?

---

