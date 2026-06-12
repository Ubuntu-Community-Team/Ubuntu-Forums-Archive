---
title: "Low Resolution after NVIDIA Driver update 304.135"
date: 2017-02-24
forum: Installation &amp; Upgrades
---

### Post by liam.gutierrez on 2017-02-24
After updating the NVIDIA driver from 304.134 to 304.135  my resolution got low 1024x768 instead of 1366x768. I tried to add a resolution with xrandr but received this error **failed to get size of gamma for output default**

I also tried to purge the new nvidia driver and reinstall but I had the same problem. Fortunately, I had Timeshift installed and could restore my OS to a previous state. I wonder if I should avoid further Nvidia updates. Or do you have any ideas how to solve that update problem?

```
            .-/+oossssoo+/-.               liam@RAT 
        `:+ssssssssssssssssss+:`           -------- 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 16.04.2 LTS x86_64 
    .ossssssssssssssssssdMMMNysssso.       Model: ET1331 P01-A2 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 4.4.0-64-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 5 hours, 23 minutes 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 2957 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 4.3.46 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1368x768 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: MATE 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: Metacity (Marco) 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: BlackMATE 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: BlackMATE [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Vivacious-Dark-Aqua [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: mate-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: AMD Athlon II X2 220 (2) @ 2.8G 
    .ossssssssssssssssssdMMMNysssso.       GPU: NVIDIA GeForce 6150SE nForce 43 
      -+sssssssssssssssssyyyssss+-         Memory: 2899MiB / 3699MiB 
        `:+ssssssssssssssssss+:` 
            .-/+oossssoo+/-.                                       


```

---

### Post by Autodave on 2017-02-24
You are not using the most current driver. Where did you get the driver form?  You can find the most current one in the repositories  I am using 375.39 from the repositories.

---

### Post by #&amp;thj^% on 2017-02-24
I think his card is out of support for that driver "NVIDIA GeForce 6150SE nForce 430"
It came out in 2005!
Suggest a upgraded (newer) card...if possible.

---

### Post by Bashing-om on 2017-02-24
liam.gutierrez; Hello:

per :
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
the 304 version driver is the correct one for that 6150SE nForce card.
However - maybe -  :
The Linux 304.* legacy driver series is the last to support the NV4x and G7x GPUs and motherboard chipsets based on them. Support for new Linux kernels and X servers, as well as fixes for critical bugs, will be included in 304.* legacy releases through the end of 2017. 
See: [http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

We should confirm that driver remains supported in the 16.10 release repository .
what returns:
```

apt list nvidia-304

```

[INDENT][INDENT]just my thoughts on the matter
[/INDENT][/INDENT]

---

### Post by liam.gutierrez on 2017-02-24
> **1fallen said:**
> I think his card is out of support for that driver "NVIDIA GeForce 6150SE nForce 430"
It came out in 2005!
Suggest a upgraded (newer) card...if possible.

This card mysteriously still gets updates in Ubuntu. I also found out "hidden" updates for this card for Windows even though it's supposedly outdated. Yet, a Chinese PC manufacturer used that old card in a 2013 model. I learned that through a friend on WeChat. The updates for Windows are "hidden" because you won't find it by regular search but through direct link [http://www.nvidia.com/download/driverResults.aspx/82758/en-us](http://www.nvidia.com/download/driverResults.aspx/82758/en-us) I was surprised when I first saw there was still another update for this card after so many years in existence. 

And as the card still gets updates in Ubuntu, I don't think it's a smart investment to buy a new card, especially if the PC I'm using is a 2009 model. Even though it's old, it rarely gives me problems. I rather replace this PC with the newest and greatest than wasting money on a graphics card now.

Maybe next time I get myself a System76 or a Dell that works nicely with Ubuntu. In the meantime, I freeze graphics driver updates. Wish a nice weekend :popcorn:                                     **Linux x64 (AMD64/EM64T) Display [Driver http://www.nvidia.com/download/driverResults.aspx/114714/en-us]("http://www.nvidia.com/download/driverResults.aspx/114714/en-us")**

                                      

                                 
                                                                                                               [TABLE]
[TR]
[TD="class: contentsummaryleft"]                                                 Version:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                 304.135[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                      Release Date:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                                                                     2017.2.14[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                                                                     Operating System:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                     Linux 64-bit                                             [/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                                                                     Language:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                     English (US)[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                                                                     File Size:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                                                                     66.53 MB[/TD]
[/TR]
[/TABLE]

---

### Post by #&amp;thj^% on 2017-02-24
> **liam.gutierrez said:**
> This card mysteriously still gets updates in Ubuntu. I also found out "hidden" updates for this card for Windows even though it's supposedly outdated. Yet, a Chinese PC manufacturer used that old card in a 2013 model. I learned that through a friend on WeChat. The updates for Windows are "hidden" because you won't find it by regular search but through direct link [http://www.nvidia.com/download/driverResults.aspx/82758/en-us](http://www.nvidia.com/download/driverResults.aspx/82758/en-us) I was surprised when I first saw there was still another update for this card after so many years in existence. 

And as the card still gets updates in Ubuntu, I don't think it's a smart investment to buy a new card, especially if the PC I'm using is a 2009 model. Even though it's old, it rarely gives me problems. I rather replace this PC with the newest and greatest than wasting money on a graphics card now.

Maybe next time I get myself a System76 or a Dell that works nicely with Ubuntu. In the meantime, I freeze graphics driver updates. Wish a nice weekend :popcorn:                                     **Linux x64 (AMD64/EM64T) Display [Driver http://www.nvidia.com/download/driverResults.aspx/114714/en-us]("http://www.nvidia.com/download/driverResults.aspx/114714/en-us")**

                                      

                                 
                                                                                                               [TABLE]
[TR]
[TD="class: contentsummaryleft"]                                                 Version:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                 304.135[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                      Release Date:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                                                                     2017.2.14[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                                                                     Operating System:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                     Linux 64-bit[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                                                                     Language:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                     English (US)[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]                                                                                                     File Size:[/TD]
[TD="class: contentsummaryright, colspan: 2"]                                                                                                     66.53 MB[/TD]
[/TR]
[/TABLE]


You may have misunderstood... my post was referring to:
> Autodave 	 	 		[INDENT] 			 				Re: Low Resolution after NVIDIA Driver update 304.135

 			 			You are not using the most current driver. Where did you get the  driver form?  You can find the most current one in the repositories  I  am _**using 375.39 **_from the repositories. 		
[/INDENT] 	

I far as I can remember this is the only driver version that works with that card "304.135"
But I think HWE stack upgrade (16.04.2) might be to much for this card now...
> Even though it's old, it rarely gives me problems.
They were nice chips at that time and I still have a couple of them that still work...but can not run any of the newer Linux OS's with.

---

### Post by liam.gutierrez on 2017-02-24
Alright, I will mark this thread as solved. I am not a big expert on hardware. I just freeze updates for graphics updates and cross my fingers my system will work until the end of 2017. That's when I plan to buy a new PC. Thanks for the info 1Fallen and Bashing-On &#128077;

---

