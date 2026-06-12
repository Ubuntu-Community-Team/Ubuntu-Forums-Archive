---
title: "Request Advice: Upgrade vs. Install"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Ingla on 2006-10-31
I came to Ubuntu with Breezy. I've been considering going to Dapper, as the time seems to have come (Ubuntu is moving on).

I've never done an upgrade before.

The problem is that I see so many posts about things going wrong with upgrades that I'm wondering whether I should just go for a clean install (seen a couple of problems mentioned about that too - like partitions not going in right).

I've been trying to replace Windows with Ubuntu completely ... almost there. Obviously, this means I've done a lot of work to get Ubuntu doing what I need. THIS IS THE MAIN DRAWBACK TO A CLEAN INSTALL ... I would need to start from scratch.

On the other hand, a lot of people seem to have had very complicated problems trying to upgrade and that could mess up a lot of what I've done anyway. I'm far from being a Linux guru, so who knows whether I could fix things!

If I go for an upgrade, I would change the repository list to the clean dapper list offered on this forum and then use the upgrade manager. Is this the best way? Is there anything else I should know?

If I used apt-get upgrade would that bring me Dapper or Edgy?

What is the safest thing to do (other than just staying with Breezy)?

Any advice greatly appreciated.

Thanks.

---

### Post by Jussi Kukkonen on 2006-10-31
Just to make you more uneasy: staying on Breezy will only be safe for another six months. That's when support will stop... ;)

You cannot upgrade from Breezy to Edgy directly, you'll have to do it in steps: Breezy -> Dapper -> Edgy. So that's another disadvantage to upgrading: it will take a long time, if you have a slow connection and a slow computer, be prepared for over 10 hours of installation (not that you have to be there, except for some configuration questions)... 

On the other hand, personally I think upgrades are great: I've done 7 or 8 upgrades on my Ubuntu machines and none of those had big problems. 

Now to the advice:
If you value your current setup a lot, my advice is to upgrade (To Dapper at least, more on that later). But this only applies if you haven't installed software from who-knows-where (compiled from source, using binary installers, etc.) or used installer scripts (like Automatix)! Since you looking for 'the safest thing to do' I'd say upgrade to Dapper and see if that's good enough for you -- it'll be supported for a long time (longer than Edgy) and it's supposed to be a more stable release.

If you decide to upgrade the instructions are here: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) (there's a similar page for Edgy if you decide to do that later).

---

### Post by Ingla on 2006-10-31
Thanks very much.

Actually, I HAVE used Automatix for several things. I'm also running at least one program under Wine (Wine installed by automatix). I have one or two external programs, but reinstalling them later would not be that terrible.

Question is: if, given what's on the system, I use Dapper repositories and hit "Upgrade" in the Update Manager, is this stuff likely to cause serious problems? This is the first time I've heard that Automatix or Wine is bad if you ever intend to upgrade. Can you elaborate?

I guess I'd better back up everything well on another drive before trying any of this.

Thanks very much.

---

### Post by KuriKai on 2006-10-31
I find that I only have problems with upgrades. Is if a package (like xserver) does not fully download.

---

### Post by xcity on 2006-10-31
My personal experience is, if you are not used to customize ubuntu, you can do a upgrade, that should be safe of doing that. But, you do customize system, by installing lots of software that are not in ubuntu official, and modify conf file, etc. You'd better no do upgrade.

---

### Post by Jussi Kukkonen on 2006-10-31
> This is the first time I've heard that Automatix or Wine is bad if you ever intend to upgrade. Can you elaborate?

When I first saw Automatix (admittedly quite a while ago) I looked at what it did and it seemed to install stuff pretty recklessly. I didn't use it then and I don't use it now so maybe I shouldn't be talking about it, but it seems others think it's not much better nowadays:

Scott James Remnant (Ubuntu Core Developer): [http://www.netsplit.com/blog/articles/2006/10/30/automatix-and-upgrading](http://www.netsplit.com/blog/articles/2006/10/30/automatix-and-upgrading)

Jonathan Carter: (Ubuntu/Edubuntu hacker): [http://jonathancarter.co.za/?p=58](http://jonathancarter.co.za/?p=58)

I'm not saying Automatix breaks your operating system, I am saying it might increase the possibility of things breaking during the upgrade: Nothing unfixable probably, but worth mentioning IMHO.

---

### Post by P_Badger on 2006-10-31
Save yourself the time and heartache and go with an install.

---

