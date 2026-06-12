---
title: "Numlockx"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by Cuber on 2005-04-11
When I try to install numlockx (apt-get install numlockx) I get a message that the program cannot be found. When I add the extra sources as discribed in the unofficial 5.04 guide I get a message that the sources cannot be found.

Anybod knows where to find the correct source for numlockx?

I tried changing config under /etc/console-tools but doesn't work for me.

Thanks.

---

### Post by lao_V on 2005-04-11
did you do sudo apt-get update after adding the extra repositories?

---

### Post by Cuber on 2005-04-11
[QUOTE=lao_V]did you do sudo apt-get update after adding the extra repositories?[/QUOTE]
 Yes, I tried both.

Neither worked, alsways says it cannot find the repostirories.

---

### Post by lao_V on 2005-04-11
I'm assuming you can connect to the net without a problem. Ubuntu repositories have been somewhat slow since hoary was released so maybe that could be an issue. Can you post what's in your /etc/apt/sources.list?

---

### Post by Cuber on 2005-04-11
Internet does work correctly. I cannot post the sources.list at the moment 'cause I am at work now, but I placed the backup of the original list back after trying, to prevent getting all the repositories via synaptic.

I know synaptic gave problems with updating as well, I also thought it would be because of slowness due to the new release. Will give it another try tonight.

---

### Post by lao_V on 2005-04-11
Well, if you had problem updating the sources then its not a problem with the package. Make sure you don't have any problem with apt-get update before searching for the package :-)

---

### Post by Cuber on 2005-04-11
I only have problems with apt-get update when I add the repositries, but I will try again tonight, I'll post here if it worked.
Do I have to update completely after adding the repositories before I try installing numlockx? I do not want all the updates from the sources, only the package I need.

---

### Post by lao_V on 2005-04-11
[QUOTE=Cuber]I only have problems with apt-get update when I add the repositries, but I will try again tonight, I'll post here if it worked.
Do I have to update completely after adding the repositories before I try installing numlockx? I do not want all the updates from the sources, only the package I need.[/QUOTE]

apt-get update doesn't update your system with all the new packages but only the packages list, so you can view them locally. apt-get upgrade will update all the installed pacakges with the new one's and apt-get dist-upgrade will upgrade your system to the latest system

---

### Post by Cuber on 2005-04-11
Works now, after adding the sources I did apt-get update and after that apt-get install numlockx.

It installed numlockx as it should! Thanks for your help!

---

