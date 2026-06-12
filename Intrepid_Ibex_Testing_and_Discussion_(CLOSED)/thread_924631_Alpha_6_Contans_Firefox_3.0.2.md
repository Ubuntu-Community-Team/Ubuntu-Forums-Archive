---
title: "Alpha 6 Contans Firefox 3.0.2?"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2008-09-19
Is This Really The Final Version Of Mozilla Firefox 3.0.2 That Is Included In Ubuntu 8.10 Alpha 6?

---

### Post by steeleyuk on 2008-09-19
Unless Mozilla release a newer version which patches a security vulnerability then yes.

---

### Post by andrewabc on 2008-09-19
Are you asking if 3.0.2 will be the released version when intrepid is released? Or if it is included in alpha 6?

[http://packages.ubuntu.com/intrepid/firefox-3.0](http://packages.ubuntu.com/intrepid/firefox-3.0)
Says what appears to be 3.0.2 dev version.

[https://wiki.mozilla.org/Releases/Firefox_3.0.2](https://wiki.mozilla.org/Releases/Firefox_3.0.2)
says it should be released September 23.

---

### Post by ubulette on 2008-09-19
Please read the complete version number, it says "build3".
We are currently tracking build6, the last known 3.0.2 candidate.
Of course, we will update it to final 3.0.2 when it's available.

---

### Post by gjoellee on 2008-09-20
yes!

However I wonder when fiefox 3.1 (beta or final) will come to Intrepid

---

### Post by steeleyuk on 2008-09-20
> **gjoellee said:**
> yes!

However I wonder when fiefox 3.1 (beta or final) will come to Intrepid

Intrepid might include a preview. Though 3.1 is more likely to appear in Jaunty.

---

### Post by jespdj on 2008-09-20
> **gjoellee said:**
> However I wonder when fiefox 3.1 (beta or final) will come to Intrepid
As far as I know the final release of Firefox 3.1 is planned for the beginning of 2009, so that will be a few months too late for Intrepid. It will certainly be ready before April 2009, when Jaunty will be released.

---

### Post by kevpan815 on 2008-09-20
When Installed As A Clean X64 Alternate CD Install Alpha 6 Says Mozilla Firefox 3.0.2 With Out The Build 3 Identifier That The Other Poster Mentioned, In Fact It Is Exactly The Same As The Screenshot.png File That Was Posted Here Earlier Today Or Yesterday, Just FYI.

---

### Post by andrewsomething on 2008-09-20
> **kevpan815 said:**
> When Installed As A Clean X64 Alternate CD Install Alpha 6 Says Mozilla Firefox 3.0.2 With Out The Build 3 Identifier That The Other Poster Mentioned, In Fact It Is Exactly The Same As The Screenshot.png File That Was Posted Here Earlier Today Or Yesterday, Just FYI.
```

andrew@andrew-testing:~$ apt-cache policy firefox
firefox:
  Installed: 3.0.2+build3+nobinonly-0ubuntu2
  Candidate: 3.0.2+build3+nobinonly-0ubuntu2
  Version table:
 *** 3.0.2+build3+nobinonly-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by ubulette on 2008-09-20
To clarify, the buildX is not mentioned in the "About" dialog or anywhere in the sources but trust me, it's not the final 3.0.2, just the 3rd release candidate (this is from a CVS tag). Think of it as 3.0.2 RC3.

We are at the 6th build now, hopefully the last/right one. If it is, it will just mean a rebuild is needed to get rid of this "buildX" tag.

---

### Post by kevpan815 on 2008-09-20
Sorry, I Am A Little Bit New At Using The Linux Command Prompt, And Using Linux In General, But Believe Me, I Have Had Plenty Of Experience Of Previous Beta Testing 4 Other Companies Including: Microsoft Windows XP, Microsoft Windows Server 2003, Microsoft Windows Vista, And Microsoft Windows Server 2008, Just 2 Name A Few Other Operating Systems That I Previously Beta Tested 4 Microsoft, As Well As Fedora 10.0 Alpha (That I Plan Not Test Anymore Until They Improve The Product Stability Of Their Fedora 10.0 Kernel), Trust Me You Guys Are Doing A Great Job At Making This A Much More Stable Alpha Operating System (I Had Lots Of Bad Luck With Fedora 10.0 Alpha), Just FYI. I Also Like Your Product Much Better Than Windows Vista Service Pack One RTM (Release 2 Manufacturing). Really, The Only Microsoft Product That I Have Not Gotten Fed Up With Is Microsoft Windows Server 2008, And It Has A Very Hugh Price Tag, Just FYI. Supposedly Microsoft Plans 2 Develop Microsoft Windows 7.0 On Top Of It's Existing Windows Vista Service Pack One Kernel, Which Means That It Will Be Just More Of The Same Rather Than Change, Just FYI.

---

### Post by mc4100 on 2008-09-20
> **kevpan815 said:**
> Sorry, I Am A Little Bit New At Using The Linux Command Prompt, And Using Linux In General, But Believe Me, I Have Had Plenty Of Experience Of Previous Beta Testing 4 Other Companies Including: Microsoft Windows XP, Microsoft Windows Server 2003, Microsoft Windows Vista, And Microsoft Windows Server 2008, Just 2 Name A Few Other Operating Systems That I Previously Beta Tested 4 Microsoft, As Well As Fedora 10.0 Alpha (That I Plan Not Test Anymore Until They Improve The Product Stability Of Their Fedora 10.0 Kernel), Trust Me You Guys Are Doing A Great Job At Making This A Much More Stable Alpha Operating System (I Had Lots Of Bad Luck With Fedora 10.0 Alpha), Just FYI. I Also Like Your Product Much Better Than Windows Vista Service Pack One RTM (Release 2 Manufacturing). Really, The Only Microsoft Product That I Have Not Gotten Fed Up With Is Microsoft Windows Server 2008, And It Has A Very Hugh Price Tag, Just FYI. Supposedly Microsoft Plans 2 Develop Microsoft Windows 7.0 On Top Of It's Existing Windows Vista Service Pack One Kernel, Which Means That It Will Be Just More Of The Same Rather Than Change, Just FYI.

Sorry if it sounds like whining, but do really you need to capitalize **every** word, really. It's hard to read, and surely must make typing rather awkward. ;)

---

### Post by kevpan815 on 2008-09-20
Sorry about my capital letter typing, it is a bad habit of mine.

---

### Post by mc4100 on 2008-09-20
> **kevpan815 said:**
> Sorry about my capital letter typing, it is a bad habit of mine.
It's funny, I can sympathize: since sometimes I find myself writing a few sentences like that (which I then have to go back and fix). Bad habits, eh?

---

