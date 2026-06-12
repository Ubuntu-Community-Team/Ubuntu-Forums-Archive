---
title: "Developer Options - Xubuntu"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by mendonca-livio on 2016-05-27
Hi guys,

I'm not sure if I'm in the correct section (tell me if I'm not) but my problem is: I can't uncheck "Pre-released updates (xenial-proposed)" in Developer Options in Software & Updates.
I don't know why it is checked since the installation and even though the pop-up for put my password appears when I try to uncheck it, it remais checked.
I concerned that it eventually let my system unstable.

Thank you in advance,
Antonio.

---

### Post by QDR06VV9 on 2016-05-27
Humm That is a bit strange it is not enabled by default but lets try this...if you do not have this installed already..
```
sudo apt install synaptic
```
Now open synaptic
And look at the top bar on the left you will see "Settings" Click that and down to "Repositories" now click that and to far right tab you will see "Developer Options" click on that 
and now see if you can UN-check the Proposed repo.
I have included Screenshots to aide.
Regards

---

### Post by kansasnoob on 2016-05-28
The proposed repo is enabled differently if you happened to use installation produced after the official release of Xenial (Xenial daily). Just to satisfy my curiosity please post the output of:

```
cat /var/log/installer/media-info
```

---

### Post by mendonca-livio on 2016-05-28
[COLOR=#C61919]**runrickus, **[/COLOR]I installed synaptic and made the procedure as you said but nothing changed. I still cannot un-check proposed repo.
but I got and error mensage

```
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
```

this appeared after I closed "Software and Updates" window and reloaded repos.

Another thing that maybe is important to say is that in the screenshots you sent to aide me was showing "Software & Updates (as superuser)" and mine was only "Software & Updates".

kind regards.

---

### Post by mendonca-livio on 2016-05-28
[COLOR=#DD4814][COLOR=#000000][kansasnoob]("http://ubuntuforums.org/member.php?u=554595"), [/COLOR][/COLOR]the requested output is

```
livio@livio-670Z5E:~$ cat /var/log/installer/media-info
Xubuntu 16.04 LTS "Xenial Xerus" - Release amd64 (20160523)livio@livio-670Z5E:~$
```

kind regards.

---

### Post by kansasnoob on 2016-05-28
Yep, as expected you used a Xenial daily image:

```
Xubuntu 16.04 LTS "Xenial Xerus" - Release amd64 (**[COLOR="#FF0000"]20160523[/COLOR]**)livio@livio-670Z5E:~$
```

The final release image for 16.04 was 20160420.1. So when you try to change that setting it just changes from a check mark to a hypen or dash. I don't know how to change that but I know proposed shows up in /etc/apt/sources.list.d in the LTS daily builds instead of in the sources.list like it would otherwise. They once had to delay a Trusty point release because they goofed and left in on which I discovered during testing and filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/1417792](https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/1417792)

I was surprised to see that they had to change the actual live image since the package change needed was livecd-rootfs.

Maybe you could "rm" that but I'm not at all sure :redface:

---

### Post by kansasnoob on 2016-06-13
Sorry for the long delay but I did add this to my personal to-do list and finally asked a question at Launchpad:

[https://answers.launchpad.net/ubuntu/+source/software-properties/+question/295277](https://answers.launchpad.net/ubuntu/+source/software-properties/+question/295277)

With any luck we'll have an answer soon :)

---

### Post by MikeMecanic on 2016-06-14
This bug is there since at least May 7[SUP]th[/SUP].  When you click to enable Proposed it is _not possible anymore_ to remove the <<enable>> check mark.  Software manager shows it enable all the time even if it&#8217;s possible to disable it by entering the password.   Kylin and Ubuntu.

                        Edit: See screenshot: There was nothing before when Proposed was disable.  I think that's the source of the bug.

---

### Post by kansasnoob on 2016-06-14
> **MikeMecanic said:**
> This bug is there since at least May 7[SUP]th[/SUP].  When you click to enable Proposed it is _not possible anymore_ to remove the <<enable>> check mark.  Software manager shows it enable all the time even if it’s possible to disable it by entering the password.   Kylin and Ubuntu.

                        Edit: See screenshot: There was nothing before when Proposed was disable.  I think that's the source of the bug.

It's not really a bug. If you read my Launchpad question you'll see I mentioned that it's been that way by design since at least Precise. The LTS daily images are not really intended to be used for stable installs but rather for testing only.

---

