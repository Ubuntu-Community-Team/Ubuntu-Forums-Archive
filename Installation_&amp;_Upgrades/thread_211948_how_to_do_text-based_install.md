---
title: "how to do text-based install"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2006-07-09
Hi all,
      How do I do a text-based install. A friend of mine has a machine which has 256 meg RAM only hence the GUI-based install doesn't work. I wanna make sure that Xserver does start up later on & he can work with the GUI. So all & any suggestions, advice & precautions to take would be welcome. Thnx in advance.

---

### Post by woedend on 2006-07-09
its not hard at all, and is faster. 

you download the alternate install cd(not the desktop install cd)...boot up the same way you would the other(have cd in tray and reboot).
Youll get a list of options, the first one is install.  The rest of the way it will hold your hand until you get to partitioning.  You can let ubuntu take over the entire hard drive or manually partition it.  The rest of the way is just filling in the blanks it asks you for.
good luck.

---

### Post by Herman on 2006-07-09
Hello, Shirish, :D
The Dapper 'Alternate' Install CD (.iso) has the text based installer and it is quite similar to the 'Breezy' text based installer we are used to, but with some changes.
I still have  the same website with illustrations to use for installing.[ Illustrated Dual Boot HomePage.]("http://users.bigpond.net.au/hermanzone/")
There is quite a lot of new stuff added and also a lot of old information still waiting to be updated. I have a new page for illustrating the process of [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html"), but I hope you won't need it. There is a thread for that here in the Ubuntu forums hosted by a very knowledgeable fellow: [Dealing with problems with the Xserver]("http://www.ubuntuforums.org/showthread.php?t=187177"),
in case you do have trouble.
Precautions? Well, if you are worried about the X-server maybe use the Live CD and go 'System -->Administration--> Device Manager and see if you can find the exact video card name listed there, that might help. Look for something including the letters 'AGP', at least, and possibly 'VGA' as well. Write down the video card's name in case you need it later. Also, mouse and keyboard and monitor info too might be helpful, but don't do too much work, nothing will probably go wrong. (Just do that if you are worried about it).
Nice to type to you again! Regards, Herman :D

---

### Post by ShirishAg75 on 2006-07-09
Hi Herman,
            I did see the webpages & u've done some remarkable work in there. While going through the [xserver-configure]("http://users.bigpond.net.au/hermanzone/p7.html") page there are  somethings which could perhaps do with some more clarity:-

1. In the xserver configure page although u've tackled the subject pretty nicely, u didn't specify should u reboot the computer after this command or is in the same session 

```
The X server is now disabled. Restart GDM
  when it is configured correctly.        
                                
                              <Ok>
``` 
Once the user clicks o.k. what does happen? For the next screen just shows another session with a fresh login. So is one supposed to reboot or the system automatically reboots. What happens here? The page is silent bout this. Include tht.

2. Also u have shown the Power PC & people having multiple devices which need to have info. in card bus identifier form. Now if this comes up by default then there should also be some app. or someway tht one can know the Bus ID. Either link to some page which has tht or have some images which show where & which are these Bus ID's with some pics. as examples.

3. Similarly some links or some other webpage which have atleast the common integrated chipsets with memory. For e.g. in my case the system (it's a laptop) has i915 & I've no idea whether the memory provided by it is same/more/lesser than the desktop. Similarly have no idea wht memory does the i915 have on the desktop. Same is the case for AMD. Perhaps some small app. or something on Windows which gives this info or some small cmd itself.

4. There is no explanation of dead keys other than given in the statement. This is confusing & doesn't really tell which is better & why?

5. Mouse are shown as 2 types :-

> [COLOR=#000000]ImPS/2        (with blue highlight rectangle)[/COLOR][COLOR=#000000]
ExplorerPS/2[/COLOR] Now again no idea which is newer/older/different or where it's used (States or Europe if there is some difference due to region?)

6. In configuring X.org server modules you didn't use/deselected 3 modules:-
   a. dbe
   b. record
   c. v41

   Although dbe's info. is given in the screen before but not of the other 2. Then again the box had said of referring to X.org documentation. Perhaps a link to the relevant page there :) ?

7. In configuring Xserver-xorg where one has to choose monitor characteristics 
    both the advanced as well as the simple options are not hyperlinked properly. Most probably where u have kept the simple & advanced they also need to be hyperlinked to the link above to function properly.
   
8. Lastly perhaps package the whole story with pages from other links in one single pdf which would be better as reference material. What do u think?

---

### Post by Herman on 2006-07-10
Hello, Shirish, Thank you for your excellent suggestions, I will try to do everything you suggested, I will start Friday morning, but I cannot do anything until then due to work commitments.

About the only problem is making it into a .pdf document. I can do that, but it doubles the amount of space I need on Bigpond's server. I have an allowance of 10240KB and currently use 60.7% of that already.
Perhaps people can click 'save page as' and save it to thier desktop, then if they want, they can paste it to an Open Office .org Writer page, click 'File', and 'Export as .pdf' themselves and even print it out if they need to.
Maybe I should make a note on each page to let people know they can do that.

All the other suggestions I will try to find either the right answers for or else appropriate links to help people. I have copied your post and will address each issue as best I can. Thank you for taking your time to look at my webpage and offer such useful advice. 
All the best! Regards, Herman :D

---

### Post by ShirishAg75 on 2006-07-10
I would suggest making the whole thing & then putting the documentation as a .torrent on torrentspy or isohunt. The good thing it'll mostly be seeded by somebody or the other one's it's in this form. Tell me what u think?

Hi herman,
           saw the newer edited page. Fantastic job there, only 2 points remain. First on the site this [link]("http://www.users.bigpond.net.au/hermanzone/p17.htm") is missing. 
Secondly, in the mouse configuration where u 've improved about the ps/2 stuff there is no mention of the trackpad or whatever is there on laptops to emulate the mice thing. Sorry can't get the right word in the mind. Perhaps something of how or what needs to chosen there could be added.

---

