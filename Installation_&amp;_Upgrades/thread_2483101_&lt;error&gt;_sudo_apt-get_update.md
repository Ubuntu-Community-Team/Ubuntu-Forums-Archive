---
title: "&lt;error&gt; sudo apt-get update"
date: 2023-01-20
forum: Installation &amp; Upgrades
---

### Post by leoxavi3r on 2023-01-20
Apple MacBook "Core 2 Duo" 2.4 (Black-08)
Identifiers: Early 2008 - MB404LL/A - MacBook4,1 - A1181 - 2242

lubuntu®&#65039; 22.04.1 LTS (Jammy Jellyfish)

HELP TO FIX

leoxavier@leoxavier:~$ sudo apt-get update
sudo password for leoxavier: 
Atingido:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Ign:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid-security InRelease                                              
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid-security Release                                                
  404  Not Found [IP: 91.189.91.39 80]
Atingido:4 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
Lendo listas de pacotes... Pronto                          
E: The repository 'http://us.archive.ubuntu.com/ubuntu lucid-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

I ALREADY DID ALL THESE::

[https://askubuntu.com/a/303261](https://askubuntu.com/a/303261)

[https://gist.github.com/niftylettuce/5619c2be9906bcbd893e1e1a25b9d795](https://gist.github.com/niftylettuce/5619c2be9906bcbd893e1e1a25b9d795)


[https://snapcraft.io/install/root-framework/ubuntu](https://snapcraft.io/install/root-framework/ubuntu)


[https://www.vivaolinux.com.br/dica/Removendo-Firefox-Snap-do-Ubuntu-2204](https://www.vivaolinux.com.br/dica/Removendo-Firefox-Snap-do-Ubuntu-2204)


[https://linuxconfig.org/how-to-install-uninstall-and-update-firefox-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-uninstall-and-update-firefox-on-ubuntu-20-04-focal-fossa-linux)

[https://askubuntu.com/questions/973520/apt-update-error-the-repository-http-us-archive-ubuntu-com-ubuntu-saucy-rele](https://askubuntu.com/questions/973520/apt-update-error-the-repository-http-us-archive-ubuntu-com-ubuntu-saucy-rele)


JUST HELP

&

HOPE

---

### Post by #&amp;thj^% on 2023-01-20
First be-careful following outdated links, your first showed:
" Asked 9 years, 7 months ago " 
Lucid is long gone from support, remove that Repo.
```
sudo add-apt-repository -r 'deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main'
```

---

### Post by leoxavi3r on 2023-01-20
Hi 1fallen thanks
I'm beginner linux user

Pls, how can i remove a repo???

---

### Post by #&amp;thj^% on 2023-01-20
We were all beginners at one time.;)
I showed you how to remove it in post# 2

---

### Post by leoxavi3r on 2023-01-20
oh thanks dude

I did this 3# method
[https://www.linuxfordevices.com/tutorials/ubuntu/remove-an-apt-repository-ubuntu](https://www.linuxfordevices.com/tutorials/ubuntu/remove-an-apt-repository-ubuntu)

and it worked
but thanks its a relief
i liked the -r trick

---

