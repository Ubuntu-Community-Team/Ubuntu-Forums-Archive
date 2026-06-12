---
title: "Firefox Crashing"
date: 2008-08-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by firstc624 on 2008-08-31
has anyone else been experianceing ff crashing very frequently?

i will click a link and for no reason it will close the whole proram again.

i assume bug, but wanted to verify w/ others b4 reporting

---

### Post by caryb on 2008-08-31
I can confirm this, one site I have to use konqueror for is [www.ingdirect.com.au](www.ingdirect.com.au) it crashes frequently:confused: I believe this to be java related in my case. Am using amd64 Kubuntu. 


Cary

---

### Post by mdawg414 on 2008-08-31
I have been having some issues as well but I believe mine has something to do with Flash Player. I recently switched to using ALSA sound and I think that has caused some problems. Perhaps the sites you are going to all have some form of flash script running?

---

### Post by David Tomic on 2008-09-01
> **mdawg414 said:**
> I have been having some issues as well but I believe mine has something to do with Flash Player.

Yes ... me too.  AMD64 as well.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1a2) Gecko/20080831152500 Ubuntu/8.10 (intrepid) Shiretoko/3.1a2

---

### Post by lexarrow on 2008-09-01
Same problem. Also AMD64.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008071816 Ubuntu/8.10 (intrepid) Firefox/3.0.1

---

### Post by David Tomic on 2008-09-01
Seems like 64-bit might be a bit of a pattern here?!?

---

### Post by firstc624 on 2008-09-01
i think you may be right, as i am running an amd64 as well, almost an exact sig of caryb.

i am looking thru launchpad now, but i don't report bugs often so if one of you want to post it, i am sure the rest of us will confirm.

i might redo this partition and see if it is casued by flash, java or whatever.

---

### Post by chacham23 on 2008-09-01
You should try Swiftfox. It didnt crush on my computer for a day now(I run alot flash sites).
I think it also faster then firefox but I not sure.. 

[http://getswiftfox.com/]("http://getswiftfox.com/")

p.s. its also runs all my addons, so no problem (for me) with that.. :)

---

### Post by Slug71 on 2008-09-01
Yep im getting it too. Specially on Myspace. I too am using AMD64.

---

### Post by beartard on 2008-09-01
Yes, Firefox is all-around nutty on my Kubuntu 64 system.  Pops up empty flash windows all over the place, freezes up the whole app while one tab is loading a page, frequent crashing, etc.  I've even started using konqueror as a browser for some sites. ;)

Still, I wouldn't install anything 3rd-party on a testing distro.  It doesn't help in the testing process to have external repos enabled or third-party software installed.

---

### Post by BackwardsDown on 2008-09-01
> Still, I wouldn't install anything 3rd-party on a testing distro. It doesn't help in the testing process to have external repos enabled or third-party software installed.

I think it is important that Flash works for all the users that are going to use Intrepid. It needs to be tested, and bugs that are caused at our side should be fixed, and bugs on the flash-side should be send to adobe.

---

### Post by avb on 2008-09-01
i think the problem is new flash plugin. Just install 9th version of flash plugin instead of a 10b. I solved my crashes that way.

---

### Post by beartard on 2008-09-01
> **BackwardsDown said:**
> I think it is important that Flash works for all the users that are going to use Intrepid. It needs to be tested, and bugs that are caused at our side should be fixed, and bugs on the flash-side should be send to adobe.
Yes, and flashplugin-nonfree is in the repositories.  I was objecting to installing swiftfox just to get around firefox's problems.

---

### Post by jerrylamos on 2008-09-01
> **firstc624 said:**
> has anyone else been experianceing ff crashing very frequently?

i will click a link and for no reason it will close the whole proram again.

i assume bug, but wanted to verify w/ others b4 reporting

I'm running Compaq 32 bit, also IBM Thinkpad 32 bit.  Firefox crashes frequently on selecting sites, frequently from AOL.com or Yahoo.com links.  This is Alpha 4, even kernel 2.6.27-2.

Jerry

---

### Post by nanog on 2008-09-01
I had the same problems (frequent crashes and multiple window pop ups) in up to date amd64. I appear to have solved them by reinstalling ubuntu-restricted-extras and then manually re-installing flashpugin-nonfree (it was not installed by ubuntu-restricted-extras bizarrely enough).

---

### Post by Nullack on 2008-09-01
> **BackwardsDown said:**
> I think it is important that Flash works for all the users that are going to use Intrepid. It needs to be tested, and bugs that are caused at our side should be fixed, and bugs on the flash-side should be send to adobe.

I think the comment the OP made about not using third party repos is very valid.

The flash plugin is available in Intrepids repos and would most certainly be there by default if it wasnt closed source software.

Testers can fully test flash using Intrepid repos and no others. Bugs from PPAs and external repos just complicate the build and defocus efforts.

---

### Post by danf_1979 on 2008-09-02
It seems this is not a 64bit exclusive issue. This happens also on my inspiron 9400 (32bit), all upgrades uptodate (2 sept).

Daniel.

---

### Post by ViRMiN on 2008-09-02
Seems to be worse since the nspluginwrapper update this afternoon.  Firefox kept crashing on sites with Flash, so I've just removed nspluginwrapper and at least the browser's now operable...

---

### Post by jlacroix on 2008-09-02
Has anyone filed a bug report already?

---

### Post by Slug71 on 2008-09-02
> **ViRMiN said:**
> Seems to be worse since the nspluginwrapper update this afternoon.

+1
Cant get into youtube at all today.

---

### Post by Nullack on 2008-09-02
Yeah the experience is poor right now but the bugs have been reported so hopefully the goodness will come from the repos soon

---

### Post by Gourgi on 2008-09-02
> **Nullack said:**
> Yeah the experience is poor right now but the bugs have been reported so hopefully the goodness will come from the repos soon

can you please post a link for the bug reports for people like who want to confirm and comment more about the bug

Edit: here is a bug report i found [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/262693](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/262693)
there is also a workaround about this in the bug's comments
> 
Downgrading to nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb makes the problem go away.

You can download it from [http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/)


> 
wget [http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb)
sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb


---

### Post by gjoellee on 2008-09-03
> **caryb said:**
> I can confirm this, one site I have to use konqueror for is [www.ingdirect.com.au]("http://www.ingdirect.com.au") it crashes frequently:confused: I believe this to be java related in my case. Am using amd64 Kubuntu. 


Cary

I have no problems, using Intrepid though:)

---

### Post by BackwardsDown on 2008-09-03
> **caryb said:**
> I can confirm this, one site I have to use konqueror for is [www.ingdirect.com.au](www.ingdirect.com.au) it crashes frequently:confused: I believe this to be java related in my case. Am using amd64 Kubuntu. 


Cary

I confirm using Ubuntu Intrepid.

---

