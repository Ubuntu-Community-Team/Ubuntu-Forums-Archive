---
title: "Can't connect to update or server denies me entry"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by clem on 2006-07-17
Hi All,
Any suggestions on how to reconnect to be able to download or to get programs needed for installations?  I have been locked out since last night, and have not been able to reconnect to their servers.

Also, has anyone used/configured/setup dansguardian on their ubuntu.  I am having difficulty getting it up and running.

Oh, and before I go and bang my head against the wall 

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

Does anyone have any idea on how to set up a Brother HL-2040 Laser Printer on  their computer?  I have been working on it all weekend and have tried everything, it recognizes the printer, says printing, paper gets jammed each time.  I have tried all the Brother drivers...nope not gonna work that way.

Thanks All & Be Well

---

### Post by mogelhead on 2006-07-17
> **clem said:**
> 
Any suggestions on how to reconnect to be able to download or to get programs needed for installations? I have been locked out since last night, and have not been able to reconnect to their servers.
...

Do you mean that you cannot use Synaptic to install new applications? Is your internet connection working for other applications, web browsing for example?

What do you mean by locked out?

Describe in more detail what you are doing and tell us the error messages you receive.

Please post the content of the file /etc/apt/sources.list

---

### Post by clem on 2006-07-17
> **mogelhead said:**
> Do you mean that you cannot use Synaptic to install new applications? Is your internet connection working for other applications, web browsing for example?

What do you mean by locked out?

Describe in more detail what you are doing and tell us the error messages you receive.

Please post the content of the file /etc/apt/sources.list
Being locked out of Synaptic has happened two or more times.  I hit reload, and it starts to get updates, and then it goes so far or not at all, and it says I have been refused by the server.  It usually works in the morning, but not in the evening.  This morning it worked fine.  I will follow your instructions if it happens again.  Thanks

---

### Post by clem on 2006-07-17
> **clem said:**
> Being locked out of Synaptic has happened two or more times.  I hit reload, and it starts to get updates, and then it goes so far or not at all, and it says I have been refused by the server.  It usually works in the morning, but not in the evening.  This morning it worked fine.  I will follow your instructions if it happens again.  Thanks
Oh sorry I forgot, I can connect to the internet & get emails.

---

### Post by mogelhead on 2006-07-18
> **clem said:**
> Being locked out of Synaptic has happened two or more times.  I hit reload, and it starts to get updates, and then it goes so far or not at all, and it says I have been refused by the server.  It usually works in the morning, but not in the evening.  This morning it worked fine.  I will follow your instructions if it happens again.  Thanks

The server from which Synaptic fetches the updates might be overloaded. It is possible to change server in the file /etc/apt/sources.list.

Since I live in Sweden, I have changed my repository server from archive.ubuntu.com to se.archive.ubuntu.com. 

[Here is a list of official mirrors]("https://wiki.ubuntu.com/Archive/OfficialMirrors").

---

