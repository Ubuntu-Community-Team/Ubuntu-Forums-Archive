---
title: "Takes a really long time to install!"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by mroussin51 on 2014-07-14
Greetings and salutations,

I have a problem and need help. When I install Ubuntu 14.04 Server it takes a really long time. Also, I noticed it takes 10 minutes for sudo apt-get update to finish. I think this happened when I tried to install Ubuntu 14.04 Server on an old machine many times one day. I think it may be somewhat of a black list.

I hope it is not due to me being ugly several years ago. I have been diagnosed with severe bipolar disorder and I get treatment in the Hospital once a Month. I am doing better now. Ubuntu is one of the simple pleasures in my life. I have others but the list is short. Not a day goes by that I don't do something on Ubuntu. I like Ubuntu so much that I have T-shirts and a hat. Please help me to fix this problem.

Thanks for reading,

Mike

---

### Post by Espionage724 on 2014-07-14
Could be the server(s) Ubuntu uses by-default are super slow. I've experienced installs that took over an hour to complete due to the installer wanting to download langauge packs around 10KB/s for whatever reason.

Both the Main and US Servers are relatively slow during normal hours from what I've seen. Was able to get my max DL speed earlier around 7AM though with the US server. No idea what's up.

In any case, could try changing the download server. Not entirely sure how to do so from Server (probably have to manually edit a file), but from Desktop, go to Software & Updates > Download From > Other... > Select Best Server (or manually choose one; I usually use mirrors.us.kernel.org) > Password > Close > Reload

---

### Post by mroussin51 on 2014-07-14
Hello again,

OK I am doing it again. When it gets to Configuring apt it hangs saying retrieving file. I suppose it is downloading from the main us repo and my ip address is getting a delay for something I did wrong. I tried many times to install 14.04 Server on a very old PC. It was hanging in the same place. I ended up unplugging the ethernet cable and it then installed. That was about two weeks ago. Thanks for not banning me completely. I would however prefer to not be punished anymore. I will continue to take my medicine and I promise to continue to be a good person.

OK, now it says "Select and install software" Retrieving file 1 of 2 and it sits and I wait.

Thanks again,

Mike

Thanks Espionage724,

I thought I was being punished. It didn't seem to take so long before the manic installs on the old box that should be decommisioned. 

Anyway, for anyone wondering how to change repositories on Ubuntu Server here goes.

Find the address to the repository that you want to use. Edit /etc/apt/sources.list and change every instance of [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) to the address you have chosen. The way I found the repository that I use was by using a desktop and accessing Software and updates. I should think there is a list somewhere also.

Very best regards,

Mike

Greetings again,

I have changed my laptop (AMD64 Trusty Tahr) back to the "Server for the United States" and executed sudo apt-get update. It ran instantly and only took seconds to download many Mb. I think I was just paranoid about being on a black list or something like that. It seems that the wait time might be due server load at the instant one accesses it. I did connect from a different gateway during troubleshooting and the delay was gone. I now think it was just coincidental.

Thanks to all that contribute to Ubuntu.

I wish you the very best,

Mike

---

