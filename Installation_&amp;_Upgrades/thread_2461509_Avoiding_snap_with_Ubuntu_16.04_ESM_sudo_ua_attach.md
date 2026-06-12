---
title: "Avoiding snap with Ubuntu 16.04 ESM sudo ua attach?"
date: 2021-05-01
forum: Installation &amp; Upgrades
---

### Post by jimdc on 2021-05-01
Hi,   Is this possible? I wanted to stick with 16.04 as I don't want to upgrade to 20.04 because of the whole Chromium+snap issue, but when I do the:sudo ua attach I see:Installing canonical-livepatch snapAt which point I ^C the ua attach as I don't know what I'm getting into, but if it ends up with a rehash of 20.04 Chromium+snap, but for 16.04, I would rather head out the door and switch distros.Anyone got an insight into this - am I being railroaded into snap usage?

---

### Post by Impavidus on 2021-05-02
If you really want to use chromium and really don't want a snap, you can install a chromium deb from a PPA. There are some available. Or maybe a flatpak, if you don't mind those.

---

### Post by deadflowr on 2021-05-02
Seems like depending on the ua contract it enables livepatch for you automatically.
You should be able to disable it and remove it.
```
sudo ua disable livepatch
```
That should disable it from the ua account.
Then try
```
sudo snap remove canonical-livepatch
```
if that works, then you can just remove snapd
```
sudo apt purge snapd
```
It'll keep snaps out unless you install a snap somehow.

If you haven't set it up up yet try using the --no-auto-enable attach option like
```
sudo ua attach --no-auto-enable <token>
```
that option should disable automatic enablement of any entitlements.
You will have enable those entitlements yourself manually though
I think you can run
```
ua --help
man ua
``` 
for more options.
Also check out this post here: [https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788]("https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788")

hope it helps

---

### Post by grahammechanical on 2021-05-02
canonical-livepatch-server-admin is a Snap application and so is canonical-livepatch-client. If you want Livepatch you will have to accept the snap application. And I expect that same thing applies to all the "services" that are part of Ubuntu Advantage such as Ubuntu Extended Security Maintenance. 

The developers at Canonical clearly believe that Snap packaging is a much more secure form of packaging than the deb package format. Security auditing the code of a deb package takes a lot of employee time. Much more time than the process of creating a snap.

We get what we pay for. As the saying goes. If we want Canonical to persist with a costly auditing process, even with their own software, then we may have to accept that there is no such thing as a free lunch when it comes to services like Livepatch and Extended Security Maintenance. We will have to pay for it even if we are only using one machine. With some other Linux distributors services like this would be part of a paid for Enterprise edition and not be available in their free to download community addition.

Regards

---

### Post by jimdc on 2021-05-04
Thank you very much for the replies, particularly the one from deadflowr with the technical information in it. I think this will do as a stop gap, but I have no idea what I will be missing out on by going down this path. I was hoping to just keep on using apt-get, which, together with an LTS, has always worked very well for me (since 8.04, and I think probably earlier).Unfortunately,  I think this is a sticking plaster solution, and looking at other distros I'll likely jump ship to Debian, as I think they seem to be a bit closer to what I would like to use.

---

### Post by Tadaen_Sylvermane on 2021-05-05
> [COLOR=#000000]Anyone got an insight into this - am I being railroaded into snap usage[/COLOR][COLOR=#000000]

No you are not. You are simply being pushed in the direction the distro wants to go. It is not a sinister plot. Things change and we change with them or we move on to one that doesn't. There is a reason Ubuntu is as popular as it is whilst also being despised by quite a few. They do what they want and that is how it is.
[/COLOR]
> [COLOR=#000000]I think this is a sticking plaster solution, and looking at other distros I'll likely jump ship to Debian, as I think they seem to be a bit closer to what I would like to use.[/COLOR][COLOR=#000000]

This is probably the best answer. At the end of the day you are at Canonical's whims so to speak. If you can't run your own distro (LFS?) or don't want to learn another one that is more consistent (Slackware? Debian? Rocky Linux *new RHEL clone*) then you deal with it. You can try to "make it fit" but that can only be done for so long. For all we know snap will follow the same path as Upstart. Good idea, bad implementation. I personally like the idea of snaps to some extent. The ability to make a single package run on any distro is a wonderful thing. Downside is loss of efficiency from shared libs as well as them being potentially very out of date. Is a trade off.

At the end of the day with a free product the developers don't owe any of us anything really. We either use it, or we don't. The more users, the better feedback for improvements. And paying for support means just that. It doesn't mean they will keep it static for people. They will "support" as needed to keep up with the changes though.[/COLOR]

---

