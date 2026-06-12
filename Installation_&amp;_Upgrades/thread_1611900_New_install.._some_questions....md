---
title: "New install.. some questions..."
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by Jynks on 2010-11-02
Hi there.... 

I am a new user of xubuntu... I chose X as I was told it is better for low end systems. Everything installed fine but I will most likely have a bunch of questions to ask over time. 

I do not know if this will be the correct place, please let me know if I should post in another section or just move me there. Also I will be posting my questions in this top thread and editing it to add more or mark them as solved so i do nto spam your board with tons of threads...

Thanks in Advance for any help.

---------------------------------------------------------------------------

--== [SOLVED](http://ubuntuforums.org/showpost.php?p=10062690&postcount=3) ==-- 
[s]Q: - Ok I am set up and installed. Is xubuntu firefox not compatible with windows firefox addons? I always used to use a addon called "[SPEEDDIAL](https://addons.mozilla.org/en-US/firefox/addon/4810/)" but it doesn't seam to install... 

<--- EDIT - Hmm.. yea can not even install [Gatherer Search](https://addons.mozilla.org/en-US/firefox/addon/12793/) witch is a just a new search function for firefox... is there another way I am ment to install Firefox addons?[/s]

--== [SOLVED](http://ubuntuforums.org/showpost.php?p=10062813&postcount=5) ==-- 
[s]Q: - In windows I always had a software firewall and virus scanner thing. I used Trend Micro's Internet Security... i have been told I do not need such things in a xubuntu install.. is that correct and if not what is a good one?[/s]

--== [SOLVED](http://ubuntuforums.org/showpost.php?p=10062513&postcount=2) ==-- 
[s]Q: - I am trying to install SKYPE (have a lot of mates on it) I go to ubuntu software centre, search skype, it is there, click more info.. it says it is the maverick-partner source... I click "use this source" and it asks me for the root password, then nothing happened... ? How do I install Skype?[/s]

--== [SOLVED](http://ubuntuforums.org/showpost.php?p=10062776&postcount=4)==-- 
[s]Q: - What is the box in the bottom right of the screen.. It looks like virtual desktop, but there is only one box.. how do I add more desktops to it? Say make it 4?[/s]

Q: - How do I set up permanent access to my windows shares?

Q: - How do I set up a directory to permanently share to my windows machines?

Q: - How do you search your hdrive for files?

--------------------------------------------------------------------------

That is it for now.. I'll add / mark solved as i continue to play with my new install... thanks in advance for any help...

--Jynks
(Be excellent to each other, and party on dudes)

---

### Post by Jynks on 2010-11-02
> **Jynks said:**
> Q: - I am trying to install SKYPE (have a lot of mates on it) I go to ubuntu software centre, search skype, it is there, click more info.. it says it is the maverick-partner source... I click "use this source" and it asks me for the root password, then nothing happened... ? How do I install Skype?

I solved this by following [this guide to installing Medibuntu](https://help.ubuntu.com/community/Medibuntu) After that I could search the "ubuntu software centre" for skype and it now had a install button.

---

### Post by Jynks on 2010-11-02
> **Jynks said:**
> Q: - Ok I am set up and installed. Is xubuntu firefox not compatible with windows firefox addons? I always used to use a addon called "[SPEEDDIAL](https://addons.mozilla.org/en-US/firefox/addon/4810/)" but it doesn't seam to install... 

<--- EDIT - Hmm.. yea can not even install [Gatherer Search](https://addons.mozilla.org/en-US/firefox/addon/12793/) witch is a just a new search function for firefox... is there another way I am ment to install Firefox addons?

I think I finally got this one as well... 

[list][*]type into search bar **about:config**
[*]click I'll be careful
[*]Type into the filter **ipv6**
[*]Right click on strong and select TOGGLE, it should now read **TRUE**
[*]**Close Firefox** (compleatly)
[*]Load Firefox, try to install addons... wow it now works (well it did for me)[/list]

---

### Post by Jynks on 2010-11-02
> **Jynks said:**
> Q: - What is the box in the bottom right of the screen.. It looks like virtual desktop, but there is only one box.. how do I add more desktops to it? Say make it 4?

yea it is a workspace.. 

[list][*]found a thing in the application bar called **settings**
[*]Click Xfce 4 Setting manager
[*]Click Workspaces
[*]Adjust to taste[/list]

---

### Post by Rubi1200 on 2010-11-02
Are you having fun? Planning on leaving any questions for us to answer?

All kidding aside, isn't it great figuring this out on your own? That is just one of the many things I love about Linux.

Perhaps there is one question I can answer:
> Q: - In windows I always had a software firewall and virus scanner  thing. I used Trend Micro's Internet Security... i have been told I do  not need such things in a xubuntu install.. is that correct and if not  what is a good one?A: completely unnecessary unless you are sharing files with Windows users or running something like a mail server. As far as a firewall is concerned; if you have a router with firewall enabled then there is no need to install/use an additional firewall on (X)Ubuntu itself.

Enjoy!

---

### Post by Jynks on 2010-11-02
> **Rubi1200 said:**
> Perhaps there is one question I can answer:
[QUOTE=Jynks;10062297]Q: - In windows I always had a software firewall and virus scanner thing. I used Trend Micro's Internet Security... i have been told I do not need such things in a xubuntu install.. is that correct and if not what is a good one?

A: completely unnecessary unless you are sharing files with Windows users or running something like a mail server. As far as a firewall is concerned; if you have a router with firewall enabled then there is no need to install/use an additional firewall on (X)Ubuntu itself.[/QUOTE]

Thanks man, I appreciate it.

> **Rubi1200 said:**
> Are you having fun? Planning on leaving any questions for us to answer?

I might be new to xubuntu but I do not consider myself new to Internet communities and feel if I want help I have to try to help myself + as u say it is fun :)


----------------

Added a new question to 1st post... .. .

Q: - How do I set up permanent access to my windows shares, as well as share a directory to my windows machines?

---

### Post by Rubi1200 on 2010-11-02
> Thanks man, I appreciate it.
You are more than welcome :)

---

### Post by Jynks on 2010-11-02
So my last question is kind of 1/2 solved... I am trying to work out how to browse my network shares to the windows systems in my house. There is a XP system and 2 Win7 systems.

Anyway, in xubuntu there is a app in **applications/system called** Gigolo .... anyway, I seam to be able to enter in a share name directly into there as a bookmark. This seams to work but seams a weird way to do it... Is there a way to browse the windows network though the **places** icon on my top application bar?

---

