---
title: "Cannot authenticate in Software Ctr. or Update Mgr."
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by robhamm on 2011-02-28
CLI upgrades and installations work just fine, as does Synaptic, etc. 

When I open Update Manager, it checks for new updates just fine, also, but when I click "Install," and the authentication window pops up, there is no field to enter the password. Closing out and retrying later, the authentication window pops up (again, without a password field), shakes back and forth rapidly, and disappears. 

The same thing happens with the software center. No error messages or anything with either of them, though.

I've tried reinstalling the update manager from Synaptic, but to no avail. 

I'm running Ubuntu 10.10 64-bit (with the server kernel, because for some reason VirtualBox seemed to want it).

Any ideas, guys?
:confused:

---

### Post by sikander3786 on 2011-03-01
I think you haven't refreshed your software index since some time. Either click the 'Check' button in Update Manager or run this command.

```
sudo apt-get update
```

[http://ubuntu4beginners.blogspot.com/2011/02/requires-installation-of-untrusted.html](http://ubuntu4beginners.blogspot.com/2011/02/requires-installation-of-untrusted.html)

---

### Post by robhamm on 2011-03-01
> **sikander3786 said:**
> I think you haven't refreshed your software index since some time. Either click the 'Check' button in Update Manager or run this command.

```
sudo apt-get update
```[http://ubuntu4beginners.blogspot.com/2011/02/requires-installation-of-untrusted.html](http://ubuntu4beginners.blogspot.com/2011/02/requires-installation-of-untrusted.html)
Thanks, but as I said in my post, checking for updates works just fine in Update Manger--There's just no password field when the window pops up to authenticate either in Update Manager or Software Center, and hence noplace to enter my password. I do updates every few days, and both updates and upgrades are still working fine if I go to the CLI or Synaptic.

Could this be a permissions issue with the the two of those?

---

### Post by sikander3786 on 2011-03-01
Can you please post a screenshot of the authentication window?

---

### Post by robhamm on 2011-03-01
> **sikander3786 said:**
> Can you please post a screenshot of the authentication window?
Sure. Here's the screenshot, and thanks for your help. Just seems odd that it would go directly to authentication failure without even giving 

[IMG]http://robhamm.com/authfailure.png[/IMG]
Seems I get the same thing when trying to authenticate for users and groups.

---

### Post by sikander3786 on 2011-03-01
Some keyring problems I think. What does it say when you expand the > Details?

Also try this. Press Alt + F2 and type

```
gksu software-center
```

Try installation and see if it is authenticated then.

---

### Post by robhamm on 2011-03-01
> **sikander3786 said:**
> Some keyring problems I think. What does it say when you expand the > Details?

Also try this. Press Alt + F2 and type

```
gksu software-center
```Try installation and see if it is authenticated then.

gksu worked, but when I try it the normal way, the auth window now shakes back and forth and disappears too quickly for me to catch, hence I can't expand the details. (Which I should have done to begin with. And did earlier, but didn't take a screen shot. I remember it gave me two links, and one started, I believe, with "Apt.")

EDIT: After changing my system password I can get the box to hold still long enough to give me the following:

[IMG]http://robhamm.com/authwithdetails.png[/IMG]

---

### Post by thapanther on 2011-03-18
Hi,

Were you able to solve this problem?

grts.

---

### Post by d3ngar on 2011-07-25
I had the same problem, but I solved it by using Synaptic...

I'll definitely install Synaptic in later Ubuntu versions.

---

### Post by isabelgobbo on 2011-10-06
Same problem with me.
I already used that commands:
sudo apt-get install --reinstall zeitgeist-datahub
sudo apt-get update
sudo apt-get upgrade
Didn't help in that problem.

---

### Post by isabelgobbo on 2011-10-06
I am from Brazil and it is happening with me too.
Ubuntu 11.04.
As far as I know to now I can't install anything by software center, update with update manager, use ubuntu tweak.
That window with authentication failure pop up quickly and shaking, impossible get a screenshot.
I don't know what I did wrong in the system to cause it but after update  Firefox for version 7 I had many problems. Firefox didn't worked and I had to reinstall many times and reconfigure it with help from a person from a forum  in Brazil.
No idea about what to do.

---

