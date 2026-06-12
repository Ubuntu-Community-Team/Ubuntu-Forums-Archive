---
title: "firefox 3.6 echofone instl gmailwon't open 10.04.02 64bit"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by ken78724 on 2011-06-15
after adding Echofone & two more add ons to firefox 3.6 gmail won't open. how can I remove the add ons? And, do you know if firefox has a help forum? 

I was able to use put [http://gmail.com](http://gmail.com) in URL and open my account w/o delay. Now firefox fails.

---

### Post by lovinglinux on 2011-06-16
> **ken78724 said:**
> after adding Echofone & two more add ons to firefox 3.6 gmail won't open. how can I remove the add ons?

If Firefox doesn't start at all, try safe mode, which will temporarily disable all add-ons. You need to run from terminal:

```
firefox -safe-mode
```

Then click "Tools >> Add-ons" and remove the problematic add-ons.

> **ken78724 said:**
> And, do you know if firefox has a help forum?

Here in the forums there a few threads I maintain specifically for Firefox troubleshooting and optimization:
  	
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")
[Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

**Other resources:**

[Official Firefox Help]("http://support.mozilla.com/en-US/home")
[Unofficial Mozilla Forum (mozillaZine)]("http://forums.mozillazine.org/index.php")

---

### Post by ken78724 on 2011-06-19
LovingLinux.... glad to find your posting as firefox froze up with me trying to read the New York Times. Now I have a warning I do not understand. Take a gander... k78724@Kproductions:~$ firefox -safe-mode
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
Am still continuing in safe mode. Am able to use Seamonkey to post here but firefox remained inoperable for 3.5 weeks. Simultaneously, I was not able to open [http://gmail.com](http://gmail.com) to read my emails using firefox but I could in Opera, Seamonkey and Chrome. 

  Should I or can you do a launchpad bug report on "WARNING: unhandled variable 18?" This is a fluke I have not seen in 12/15 years using firefox.

Again, many thanks! But simultaneously, I am sad that an immediate answer on the inability to use the browser to perform routine google functions. I thought. Hmmmm firefox is fighting google. 

Ken

---

### Post by lovinglinux on 2011-06-19
> **ken78724 said:**
> LovingLinux.... glad to find your posting as firefox froze up with me trying to read the New York Times. Now I have a warning I do not understand. Take a gander... k78724@Kproductions:~$ firefox -safe-mode
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
Am still continuing in safe mode. Am able to use Seamonkey to post here but firefox remained inoperable for 3.5 weeks. Simultaneously, I was not able to open [http://gmail.com](http://gmail.com) to read my emails using firefox but I could in Opera, Seamonkey and Chrome. 

  Should I or can you do a launchpad bug report on "WARNING: unhandled variable 18?" This is a fluke I have not seen in 12/15 years using firefox.

Again, many thanks! But simultaneously, I am sad that an immediate answer on the inability to use the browser to perform routine google functions. I thought. Hmmmm firefox is fighting google. 

Ken

Get Firefox 4. See the Mega thread for instructions. The 3.6 version will be upgraded soon.

Firefox 4 is a lot better than 3.6.

BTW, Firefox 5 will be released in 2 two days.

---

### Post by ken78724 on 2011-06-19
could not enter tools and addons directly. all it wanted to do was update. so I clicked on tools and error console where I finally found a way to delete the listing with about 80 errors. 

however, this does not settle the issue about firefox failing to log in to my email account once I place [http://gmail.com](http://gmail.com) in the firefox url.

I believe there's a bug raising its head. 

:popcorn: Part of the issue is solved. Am pleased you monitor firefox. thanks for the hard work!

---

### Post by ken78724 on 2011-06-19
had not seen notice 4.0 or 5.0 are in the wing.

---

### Post by ken78724 on 2011-06-19
what did you add to Ubuntu Natty 11.04 to get Kubuntu 11.04 Natty Narwhal. Over this week end I had wanted to add falkTX's kxstudio ppa that builds one 10.04.03 rather than run in 10.04.02.

Ran into a snag and have an abssessed tooth. Those two and a back log kicked me out of bed. 

thanks again for making firefox run

---

### Post by ken78724 on 2011-06-19
Hi: firefox remained froze up. still cannot open and read New York Times articles without babying the process. I do not see the errors involved. I fear the gmail will still not open. apologies but I must relax this abssessed tooth and rest it out. 
ken

---

### Post by lovinglinux on 2011-06-19
> **ken78724 said:**
> had not seen notice 4.0 or 5.0 are in the wing.

Firefox 5 is already in the Ubuntu proposed repository.

About the releases, see [https://wiki.mozilla.org/Releases](https://wiki.mozilla.org/Releases)

> **ken78724 said:**
> could not enter tools and addons directly. all it wanted to do was update. so I clicked on tools and error console where I finally found a way to delete the listing with about 80 errors. 

however, this does not settle the issue about firefox failing to log in to my email account once I place [http://gmail.com](http://gmail.com) in the firefox url.

I believe there's a bug raising its head. 

:popcorn: Part of the issue is solved. Am pleased you monitor firefox. thanks for the hard work!

Deleting the errors in the Error Console doesn't fix anything. That is just a log that helps you find and troubleshoot problems. 

When you try to open Gmail, what exactly happens? The page keeps loading, Gmail gives some error warning or what?

If you are experiencing connection issues, [disable ipv6]("http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions").

> **ken78724 said:**
> what did you add to Ubuntu Natty 11.04 to get Kubuntu 11.04 Natty Narwhal. Over this week end I had wanted to add falkTX's kxstudio ppa that builds one 10.04.03 rather than run in 10.04.02.

See [http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

> **ken78724 said:**
> Ran into a snag and have an abssessed tooth. Those two and a back log kicked me out of bed.

I had a similar problem two weeks ago. Terrible pain. I hope you recover soon.

> **ken78724 said:**
> thanks again for making firefox run

You are welcome.

> **ken78724 said:**
> Hi: firefox remained froze up. still cannot open and read New York Times articles without babying the process. I do not see the errors involved.

Install [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") and [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") or [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") to block unnecessary stuff. See if that helps.

---

### Post by ken78724 on 2011-06-22
Amigo,,,,, Muito Obrigado e Bom Dia! Ken

---

### Post by lovinglinux on 2011-06-22
> **ken78724 said:**
> Amigo,,,,, Muito Obrigado e Bom Dia! Ken

You are welcome. Have a nice day too.

---

### Post by ken78724 on 2011-06-26
Bom Dia LovingLinux: No e posivel,, Yes am still having trouble with the original problem and gmail won't open. & I do not find Firefox 5, which you describe... Firefox 5 is already in the Ubuntu proposed repository. About the releases see [https://wiki.mozilla.org/Releases](https://wiki.mozilla.org/Releases). I did not find a specific release. So, I went to synaptic file manager where I selected reinstall Firefox. F 5 does not come up in synaptic file manager; Nada. Hmmmm. Am still nursing the tooth ache so I may a bit getting back here. 

Many thanks. Ate Logo. Ken

---

### Post by lovinglinux on 2011-06-26
> **ken78724 said:**
> Bom Dia LovingLinux: No e posivel,, Yes am still having trouble with the original problem and gmail won't open. & I do not find Firefox 5, which you describe... Firefox 5 is already in the Ubuntu proposed repository. About the releases see [https://wiki.mozilla.org/Releases](https://wiki.mozilla.org/Releases). I did not find a specific release. So, I went to synaptic file manager where I selected reinstall Firefox. F 5 does not come up in synaptic file manager; Nada. Hmmmm. Am still nursing the tooth ache so I may a bit getting back here. 

Many thanks. Ate Logo. Ken

Firefox is only in the official repos for Natty users. You need to use a ppa, since you are using Ubuntu Lucid. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by ken78724 on 2011-07-24
After chrome installed on 11.04 Natty, FF fails to allow me to list a URL How can I solve this fowl up? I uninstalled and reinstalled and have no difference. Is google developers doing this to FF? :confused:

What's next?

---

### Post by lovinglinux on 2011-07-24
> **ken78724 said:**
> After chrome installed on 11.04 Natty, FF fails to allow me to list a URL How can I solve this fowl up? I uninstalled and reinstalled and have no difference. Is google developers doing this to FF? :confused:

What's next?

What do you mean by list an URL?

---

