---
title: "install ubuntu on 64gb ssd(msata) and 320 hdd(7200rpm)"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by micatske on 2012-07-01
Hey,guys. I am just upgrade my x220 with  a 64gb ssd(msata) and I am going to reinstall my Ubuntu on it. But here come to the problem I use Ubuntu as only system, So there will be a lot of software or other things in the system, so 64gb is far from needs. I am comfusing which file should I install in SSD.
  I know the /home will be install in HDD.
 what others? such as /usr /opt,etc. Because I have matlab.mathmatic,autocad and tons of software to run. I don't think there're enough space in ssd. So what files should i put in ssd and what should i put in HDD.

 Thanks for your advice. And since this is the first time for me to use SSD, are there any tips for me? Thank you very much

---

### Post by DJ_Max on 2012-07-01
Install /home on the HDD and everything else on the SSD

---

### Post by oldfred on 2012-07-01
I know autocad does not run in Ubuntu. Are you installing Windows in virtual box?

I have 12.04 and 12.10 each in 30GB / partitions on my 60GB SSD. I have a lot of applications and have used about 7GB of the 25 allocated to each. I do keep /home inside / (root) but move all data folders to my rotating drives so /home is tiny. My /home is about 1GB with 3/4 of that .wine which I have not moved to the rotating drives.

---

### Post by micatske on 2012-07-01
> **oldfred said:**
> I know autocad does not run in Ubuntu. Are you installing Windows in virtual box?

I have 12.04 and 12.10 each in 30GB / partitions on my 60GB SSD. I have a lot of applications and have used about 7GB of the 25 allocated to each. I do keep /home inside / (root) but move all data folders to my rotating drives so /home is tiny. My /home is about 1GB with 3/4 of that .wine which I have not moved to the rotating drives.

Yeah, I will install virtualize in ubuntu. Is there any goodness for me to install it on Ssd? I found that though mine has 8gb memory card,still work slowly when running vm.

---

### Post by oldfred on 2012-07-01
I have not use virtual memory to install anything, on my short list of things to try.

What is issue with 8GB flash drive?

---

### Post by sunbird on 2012-07-03
I'm considering doing the exact same thing on a x220. I'm wondering what make/model of msata SSD you decided to get and whether you've had any issues with it?

Or does anyone else have suggestions for msata SSDs to avoid for use on an ubuntu-only system?

**Edit:** I'm looking at the [40 GB Intel 310]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820167039").

---

### Post by adad on 2012-08-04
I just needed one partition for my SSD. I configured my SSD under Ubuntu 12.04 according to this blog.

[http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/](http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/)

I used my swap partition on the HDD. Home on the HDD, the rest on SSD.

---

