---
title: "Installing MyUnity"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by TheOnlyNameless on 2013-04-12
I am currently running Ubuntu 12.10 on a Dell Inspirion 1545. I attempted to install MyUnity follo[FONT=arial]wing this tutorial: [/FONT][http://www.wikihow.com/Install-My-Unity-Configuration-Tool-on-Ubuntu](http://www.wikihow.com/Install-My-Unity-Configuration-Tool-on-Ubuntu)
[FONT=arial]First I ran 
[COLOR=#414141]sudo add-apt-repository ppa:myunity/ppa ,
[/COLOR][/FONT][FONT=arial]This worked fine. Then I wanted to update my system using
[/FONT][COLOR=#414141][FONT=Arial]sudo apt-get update
[/FONT][/COLOR][FONT=arial]This however caused an error to pop up:
[/FONT]W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

So now is where I need help. I can't install MyUnity using 
[COLOR=#414141][FONT=Arial]sudo apt-get install myunity[/FONT][/COLOR]
Since the file cannot be found!
I also cannot find MyUnity in the Software Centre.
Does anyone know of a way to either remove the MyUnity files from my Computer (Using synaptic ?) or to properly install MyUnity?

---

### Post by fantab on 2013-04-12
I don't think MyUnity is supported in 12.10. Instead use [Ubuntu Tweak Tool]("http://www.webupd8.org/2012/11/ubuntu-tweak-gets-full-ubuntu-1210.html").

---

