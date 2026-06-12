---
title: "Can the Internet Explorer 10 or IE10 be installed on Ubuntu?"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by Joe999 on 2012-10-01
Hi guys,

Trying to figure out whether the Internet Explorer 10, in short form IE10, can be installed on Ubuntu (or in the other version of Linux) or not? Has anyone tried it successfully. Can be installed in the first place?

I have searched this topic on Google, but surprising did not find a single thing related to it.

Kindly reply, this is my first post in the forum.

Thanks :)

---

### Post by Wim Sturkenboom on 2012-10-02
It will not natively run in Linux. You can give it a try in wine.

Seeing the results for IE8 and IE9 ( [http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25) ), I think you're wasting your time ;)

---

### Post by MARP1961 on 2012-10-02
Why bother with Internet Explorer? Even on Windows, people are increasingly opting for Chrome (Chromium in Ubuntu repositories) or Firefox.

---

### Post by Mark Phelps on 2012-10-02
> **Joe999 said:**
> Hi guys,

Trying to figure out whether the Internet Explorer 10, in short form IE10, can be installed on Ubuntu (or in the other version of Linux) or not? Has anyone tried it successfully. Can be installed in the first place?

IE10 won't even run on Vista -- so it should be no surprise that you won't be able to use it in Linux.

---

### Post by daslinkard on 2012-10-02
> **Mark Phelps said:**
> IE10 won't even run on Vista -- so it should be no surprise that you won't be able to use it in Linux.

There is too much hype around IE 10 and will be another version of IE that will be exposed to hackers and malicious users across the world.  If you're already using Linux why degrade your system by going down to the lowly ranks of a Microsoft product such as IE?

The world will be right when Linux becomes more widely used.  I have seen the Windows 8 demo and I look forward to the discontent that many users will have with the new Windows.  The days of XP are over and I think the changes made to the OS may be too drastic for a lot of your old school XP users.

---

### Post by Joe999 on 2012-10-02
Thanks you all for your replies guys. Appreciate it. 

I want Internet Explorer, particularly more secure IE 10, for XDK websites like this [http://www.zerodha.com/back-office](http://www.zerodha.com/back-office) . Click the backoffice button, it will open in IE ONLY because it has something called XDK inbuilt. 

The link was just an example. There are other websites I know that use XDK, and Firefox, Chrome etc. have no alternative of it. I have already Googled about it.

Can you suggest me a solution? I have very recently moved to Ubuntu.

Thanks

---

### Post by vasa1 on 2012-10-02
> **Joe999 said:**
> ...

I want Internet Explorer, particularly more secure IE 10, ...
Can you suggest me a solution?...
If you need IE10, then Ubuntu or Linux in general may not be for you. If you still want to keep Ubuntu, you could learn all about virtualization and install Windows 8 (with IE 10), if that is possible, in a virtual machine running on your Ubuntu OS.
Otherwise, just use Windows 100% especially if you do a lot of work involving sites like those you mention.

---

### Post by oldfred on 2012-10-03
Frankly any web site that is IE only, in today's world with many other browsers would not be a web site I used. I would be worried about all the other security issues that site might have. 
And Europe requires a browser selection screen when you boot Windows for the first time,  so IE is not the only browser out there.

---

### Post by kurt18947 on 2012-10-03
Is this the XDK you're referring to?

 [http://www.appmobi.com/?page_id=304](http://www.appmobi.com/?page_id=304)

> If you use the power of HTML5 and appMobi&#8217;s cross platform tools,  you&#8217;ll only need to write your app once to address ALL of the other  stores your app can sell in. 
 HTML5 is the &#8216;lingua franca&#8217; of cross platform app development.  appMobi&#8217;s free tools enable your HTML5 hybrid app an be built for iOS  Tablets, iOS Smartphones, Android Tablets, Android Smartphones, Google  Play Store, Amazon App Store, Mozilla App Store, Facebook App Center,  Google Chrome store. More outlets are being added monthlyThat sure doesn't sound like something that would be IE10 only.  The other XDK that shows up is Xbox Development Kit.  That doesn't seem like what you're referring to though.

---

### Post by vasa1 on 2012-10-03
> **kurt18947 said:**
> Is this the XDK you're referring to?
...
When you click on the link that OP provided and then on the "backoffice button", there's this error message:
**Sorry. You need a browser that supports XDK. Please use IE**
Unfortunately, many sites in India are (still) IE-specific or don't render well with other browsers. In some cases, it's just a matter of spoofing the user-agent string but I didn't look into the matter. In other cases, spoofing doesn't work.

Market forces will teach them a lesson. It's a matter of time.

BTW, it's not uncommon to still encounter several Indian sites carrying the "This site works best with IE6". Yes, IE6.

---

### Post by vasa1 on 2012-10-03
> **Joe999 said:**
> ...
Kindly reply, this is my first post in the forum.
...
You've also posted at askubuntu.com here: [http://askubuntu.com/q/195371/25656](http://askubuntu.com/q/195371/25656)

---

### Post by kurt18947 on 2012-10-03
> **vasa1 said:**
> When you click on the link that OP provided and then on the "backoffice button", there's this error message:
**Sorry. You need a browser that supports XDK. Please use IE**
Unfortunately, many sites in India are (still) IE-specific or don't render well with other browsers. In some cases, it's just a matter of spoofing the user-agent string but I didn't look into the matter. In other cases, spoofing doesn't work.

Market forces will teach them a lesson. It's a matter of time.

BTW, it's not uncommon to still encounter several Indian sites carrying the "This site works best with IE6". Yes, IE6.

I've seen that on U.S. sites as well, along with "requires  Windows ME :shock:, Windows 2000, Netscape 4......" I have no idea when those sites were last revised.

---

### Post by KaisarCode on 2013-06-25
Some of the people here are web developers.
We need to test our projects in IE.

Of course I personally use another browser!

---

### Post by kurt18947 on 2013-06-25
I don't know that there's much choice except to have Windows running either dual boot or in a virtual machine.  I have a multi-boot setup but I suspect it'd be quicker if you need to switch between OSs frequently to have a VM.

---

### Post by RavenLX on 2013-06-25
I don't think IE 10 will work in Linux but I used PlayOnLinux to set up Internet Explorer 8 and got it working. They have it as one of the pre-configured applications you can install within PlayOnLinux. I found it worked out ok. YMMV though and sometimes it could end up a corrupted window or crash. They also have pre-configured IE 6 as well, I think. You will need WINE installed, of course.

Here's my tutorial on setting up a PlayOnLinux virtual drive. Then you just instead of clicking the "install non-listed software" click on the "internet" icon at the top and find Internet Explorer in there.
<snip>

I found that installing IE from the "internet" icon in PlayOnLinux lets you actually connect IE to the internet and use it as a normal web browser.

---

### Post by simptechmike on 2013-08-24
> **Joe999 said:**
> Thanks you all for your replies guys. Appreciate it. 

I want Internet Explorer, particularly more secure IE 10, for XDK websites like this [http://www.zerodha.com/back-office](http://www.zerodha.com/back-office) . Click the backoffice button, it will open in IE ONLY because it has something called XDK inbuilt. 

The link was just an example. There are other websites I know that use XDK, and Firefox, Chrome etc. have no alternative of it. I have already Googled about it.

Can you suggest me a solution? I have very recently moved to Ubuntu.

Thanks

You won't need IE to access this site. To avoid getting the message claiming you need IE, install the firefox plugin User Agent Switcher. With this plugin, you can "pretend" to be using Internet Explorer 7 on Vista and avoid the message. This just might work for any IE only site out there.

---

