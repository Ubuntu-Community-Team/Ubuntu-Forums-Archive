---
title: "Citrix ICA Client throws an error"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by ki-vivekanandan on 2016-02-20
Hello,

I am a new Ubuntu user and having an hard time to get Citrix ICA Client installed and working. Although I was able to install ICA Client and certificates, I get the following error when I try to open the .ica file.

you have not chosen to trust "GeoTrust SHA256 SSL CA", the issuer of the server's security certificate {SSL Error 61}

I am trying to use Mozilla Browser. Any help would be much appreciated. Thanks

---

### Post by MAFoElffen on 2016-02-21
Go to GeoTrust's support knowledgebase >[Here]("https://knowledge.geotrust.com/support/knowledge-base/index?page=content&id=SO26895&actp=LIST&viewlocale=en_US")<

There is instructions to download and accept their current ssl's based on which cert your browser is has, and needs updated. There is instructions as to the browser on how to accept it. (Has note there for ForeFox...)

---

### Post by MAFoElffen on 2016-02-21
Go to GeoTrust's support knowledgebase >[Here]("https://knowledge.geotrust.com/support/knowledge-base/index?page=content&id=SO26895&actp=LIST&viewlocale=en_US")<

There is instructions to download and accept their current ssl's based on which cert your browser is has, and needs updated. There is instructions as to the browser on how to accept it. (Has note there for ForeFox...)

That is assuming that you also ran these two commands when you did your installation, but are now still having CA problems:
```

sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts/

```

---

### Post by MAFoElffen on 2016-02-21
Go to GeoTrust's support knowledgebase >[Here]("https://knowledge.geotrust.com/support/knowledge-base/index?page=content&id=SO26895&actp=LIST&viewlocale=en_US")<

There is instructions to download and accept their current ssl's based on which cert your browser is has, and needs updated. There is instructions as to the browser on how to accept it. (Has note there for ForeFox...)

That is assuming that you also ran these two commands when you did your installation, but are now still having CA problems:
```

sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts/

```
I also found you some tips/hints from someone's tutortial"
> 
Click on the &#8220;open menu&#8221; icon in the top right corner of the Mozilla Firefox interface. Then click on the Add-ons icon. Click on Plugins and then on &#8220;Citrix Receiver for Linux&#8221;. Choose &#8220;Always activate&#8221; option next to &#8220;Citrix Receiver for Linux&#8221; Attempt to access your Citrix site. If Firefox prompts you to open a .ica file, choose to open it with /opt/Citrix/ICAClient/wfica.sh, and tell Firefox to remember that choice.


---

### Post by ki-vivekanandan on 2016-02-21
Hello MafoElffen,

I appreciate your interest taking time to solve my query. Unfortunately none of the above solutions work. I had to remove Citrix ICA Client to the scratch and reinstall it. The problem I had earlier was because i installed 64 bit and I reinstalled it with 32 Bit which did the trick. As some of the forums suggest I used the "Details" app to get to know the bit number.

Thanks for your time in assissting this issue. 

Vivek

---

