---
title: "Help upgrading from Dapper to Edgy"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by rdoolen on 2007-01-12
I have tried to upgrade to Edgy... and failed...twice.

Now I want to try again. I am mainly looking for advice on how to do this before I start again. Also, how can I document what I Have done to aid in trouble shooting.

I am running the x386 version of 6.06 on an AMD 64bit machine. The 64bit version lacked too many things I wanted.

In my previous atempts, I had trouble with the installation. It kept freezing in the middle. It was unrecoverable, and was a mess if I rebooted. I am getting good at restoring from backup. 

It turns out, the upgrade HATES UIM. I don't know why. I read you could fix something and it would work, but I decided to uninstall it. It worked. I got all the way to Edgy. 

I ran it for a couple of days. It was just too unstable. It would seem fine for a while and then just freeze. Sometimes it wouldn't boot properly, it would just go black when it should have started X. I think my issues were due to video card settings. After the upgrade, the 3D acceleration was broken. This is apparently a know issue. I have an ATI 8500DV. I followed the wiki at:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

It seemed to be installed correctly. I got the correct output from fglrxinfo, but this really made things bad. Iit would freeze within 5 minutes. Even when I went back to the original settings, it was unstable as I described above. 

So, after a few days, I punted. I reloaded my backup.

---

### Post by Sense on 2007-01-13
When I updated with the standard update program, I had also problems. But because I had my /home on a diggerent partition, I could afely install a clean dapper. If you have your /home also on a different partition, maybe the best way to upgrade is to make a clean install and than change in sources.list every dapper into edgy. Than there are less dependecy conflicts and less packages to update, so the update costs less time.

---

### Post by rdoolen on 2007-01-13
This seems like a good idea, but one thing confuses me. I understand that the /home is preserved by putting it on a separate partition. But, how do I save my other settings, like things I have changed in the /etc or /usr. Can these things be saved or would I have to redo everything.

---

