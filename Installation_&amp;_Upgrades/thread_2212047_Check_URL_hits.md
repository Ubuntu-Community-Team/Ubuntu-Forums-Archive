---
title: "Check URL hits"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by derekchung on 2014-03-19
We have a web server which using LAMP , we want to get the statistics  about the hits rate of the URL , I just know cpanel , awstats could do  that , but I don't know what is the difference of these two packages , I  would like to ask what packages that I should install to do that ?   besides , if the URL is a external link ( not hosted by our company )   eg. <a href="https://www.google.com/testing/...."  </a> , is it possible get the  statistics summary ? thanks 

thanks

---

### Post by TheFu on 2014-03-19
If you don't hold the webpage, then you need to act like an ad compnany and get that other page to have a "webbug" included to count hits.

cpanel is a controlling interface, not tracking interface.
Use webalizer or awstats to gather stats or google-analytics if you don't care about the visitor's privacy.

---

### Post by derekchung on 2014-03-19
thx reply ,

Sorry to my fool , do you mean if I am not web hosting company , I should not use cpanel ? if only want to get the hit statistics  , it should not use cpenal ? thanks

---

### Post by TheFu on 2014-03-19
exactly.

---

### Post by derekchung on 2014-03-19
thx reply ,

The links that I would like to know the hit rate are commonly used by  any user ( any user can access this link from any IP , any domain ... ) ,  if what I would like to know the statistics summary is only the hit  which redirect from our domain ( the user access our webpage first ,  then click the URL , what I would like to know is how many of this kind  of click ) , is Google Analytics or any method can do that ? thanks

---

### Post by TheFu on 2014-03-19
If the link isn't to your site, them you cannot know about it.

However ... if you study how google does their search results links, you will see they track these by being slightly sneaky. You could do the same.

I've never used google-analytics and I block it at the router it is sooooo veeeeeery offensive to me. My and my users' privacy is worth at least that.

---

