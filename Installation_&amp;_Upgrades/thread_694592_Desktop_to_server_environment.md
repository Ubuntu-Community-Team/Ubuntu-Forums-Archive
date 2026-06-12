---
title: "Desktop to server environment?"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by olbaidle on 2008-02-12
Dear guides:-)

Guys after browsing through the forums i could not really find and specific answers to my question. That is i have Ubuntu desktop installed on my new machine, i wanted to do this to help me learn a bit of Linux an i have enjoyed that. However i want to move from Ubuntu Desktop to Sever smoothly and easily....so does this mean i have to uninstall Ubuntu completely and start all over again? 

This for me is where it got complicated? I have a dedicated machine with ubuntu installed no Dual boot rubbish. How to actually remove it? i have seen various options all of which component-wise i am not all that familiar with (KEEP GrUB/remove GrUB....me no no) I was looking at formatting the Hard drive is that wise? 

Any help is much appreciated.

---

### Post by DavidTangye on 2008-02-12
In theory, you just remove the package 'Ubuntu Desktop', then install the server packages that you want. Try installing the package 'ubuntu-serverguide' and see what it says about what meta packages make up a server.

---

### Post by zvacet on 2008-02-12
>  However i want to move from Ubuntu Desktop to Sever smoothly and easily

You ca do that by going to **synaptic>edit>mark packages by task>LAMP**.That way you will have desktop and server in the same time.If you decide that you don´t need GUI anymore

```
sudo apt-get remove ubuntu-desktop
```

---

### Post by olbaidle on 2008-02-13
> **zvacet said:**
> You ca do that by going to **synaptic>edit>mark packages by task>LAMP**.That way you will have desktop and server in the same time.If you decide that you don´t need GUI anymore

```
sudo apt-get remove ubuntu-desktop
```


SO is that then a case of just popping in the Server CD i downloaded going through the install and then removing the desktop? It cant be that easy can it?

My idea is to run the server and put a VM server on it to run differnt types of LINUX as VM's.

---

### Post by olbaidle on 2008-02-13
Hi David,

Thanks, this my sound silly but how on earth do i rmove the desktop package? Is that to sudo apt-get remove ubuntu-desktop"' as Zvacet posted?

And thn chuck the Server CD in?

I am beginning to realise i have alot of options here.......chooosing the right one may be difficul;t fr me...

---

### Post by DavidTangye on 2008-02-14
Yes, remove the package with apt-get, or synaptic gui - same thing really, Synaptic is the gui equivalent and is a friendly way to find packages.

I do not think you should need to use the server CD. Once you are up and running, the server packages etc are available from the repositories online, where all your updates will come from. Start Synaptic and search for packages like 'server'. Get the ubuntu-server guide (itself a package, so you install it and read its files), and see what packages you want to get and why.

---

### Post by DavidTangye on 2008-02-14
No, dont install the system again with the server CD. You already have Ubuntu installed. Just fine-tune the packages you want now, eg add server packages and remove gui ones if you wish

---

### Post by zvacet on 2008-02-14
Yes,it is simple.You are runing desktop version and you want to run server.As I  posted to you install LAMP with synaptic and configure it.That is your server.After that remove GUI with 

```
sudo apt-get remove ubuntu-desktop
```

---

### Post by k3lt01 on 2008-02-15
Thanks so much for this, I have been wondering was there an easy way to do it and now I know just through doing a search for LAMP. Now I can get :guitar: rocking.

---

