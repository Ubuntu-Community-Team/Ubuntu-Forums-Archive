---
title: "Ubuntyu 10.04  No email"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2010-04-30
Clean install Ubuuntu 10.04 on SONY VAIO VGN-NS105N.
I can't get either Evolution or Thunderbird programs to send or receive.
I have Ubuntu 9.04 installed in another partition and everything works there. I carefully copied the setup from 9.04 to 10.04. 
Of course the Internet is connected, and "Network Tools" work as advertised.
I am wondering if I am alone with this problem, or are there others?:confused:

---

### Post by omega13a on 2010-04-30
You are not alone. When I went to go check thunderbird's error console, I see these two errors occurring repeatedly:
> Error: [Exception... "'Initialization failed' when calling method: [nsILoginManagerStorage::init]"  nsresult: "0x8057001e (NS_ERROR_XPC_JS_THREW_STRING)"  location: "JS frame :: file:///usr/lib/thunderbird-3.0.4/components/nsLoginManager.js :: anonymous :: line 129"  data: no]
Source File: file:///usr/lib/thunderbird-3.0.4/components/nsLoginManager.js
Line: 129
> Error: this._storage is null
Source File: file:///usr/lib/thunderbird-3.0.4/components/nsLoginManager.js
Line: 534

Any help would be greatly appreciated!

---

### Post by thelugnut on 2010-05-01
My problem is solved.
I don't know if this will help anyone, but here it is.
My ISP can be listed in a variety of names such as, "smile", "015", "zahav".I was using the name I used in Ubuntu 9.04. Nothing worked either with Thunderbird or Evolution.
On a hunch, I selected another name and everything works fine. 
Why? I haven't the slightest clue.
We live in a strange and wonderful world.:guitar:

---

