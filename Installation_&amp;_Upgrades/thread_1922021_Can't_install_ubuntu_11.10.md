---
title: "Can't install ubuntu 11.10"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by musabhai6012 on 2012-02-07
I am trying to install ubuntu  11.10 on my hp laptop(core i7 2nd gen processor, 8gb ddr3 ram, 500gb hdd) in which i already have windows 7. i want to make it dual bootable. when i go to the partition scrren from from ubuntu . It doesn't shows the previously installed windows and showing my hdd as 500 gb free space. 
 Please have a look at the link below. These are screenshots of my problem.

1st: [https://kumxeg.blu.livefilestore.com/y1p43HjmgYXl7Djg0esb3vATPsgmvqkNWKyD4b0QSBcFEQm374j3WDIGQLlxWEdhR5NVsQs5lCzO-_V-h2EDoYrgxefqlcXoIwd/1st.jpg ](https://kumxeg.blu.livefilestore.com/y1p43HjmgYXl7Djg0esb3vATPsgmvqkNWKyD4b0QSBcFEQm374j3WDIGQLlxWEdhR5NVsQs5lCzO-_V-h2EDoYrgxefqlcXoIwd/1st.jpg )

As in this image, u can see that the home folder shows that I have 4 partitions along with a system partition which is created by windows 7 during installation.

2nd: [ https://public.blu.livefilestore.com/y1px2F-tdlWE4SRow5kazQgnUjiP4ETWyQkR7M1RK916w_jSj3bqFtGlepoGOmus7_SrYrOZNj5cUnPMstLBr4x3A/2nd.jpg ]( https://public.blu.livefilestore.com/y1px2F-tdlWE4SRow5kazQgnUjiP4ETWyQkR7M1RK916w_jSj3bqFtGlepoGOmus7_SrYrOZNj5cUnPMstLBr4x3A/2nd.jpg )

3rd: [ https://public.blu.livefilestore.com/y1pW7OqlxxbTo3GM2iR6jx1U1dV3l9MFsE35n6iYbK82M_HKEa80l8w515bt1_l-jOgoSWKFcXDaTr7r8Jonte1xw/3rd.jpg ]( https://public.blu.livefilestore.com/y1pW7OqlxxbTo3GM2iR6jx1U1dV3l9MFsE35n6iYbK82M_HKEa80l8w515bt1_l-jOgoSWKFcXDaTr7r8Jonte1xw/3rd.jpg )

But here, my disk is shown as 500 gb free space.

Help me please..

---

### Post by Rodney9 on 2012-02-07
Select the something else and it will give you the option to install Ubuntu alongside Windows.

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://goo.gl/pEs84](http://goo.gl/pEs84)

Rodney

---

### Post by musabhai6012 on 2012-02-07
> **Rodney9 said:**
> Select the something else and it will give you the option to install Ubuntu alongside Windows.

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://goo.gl/pEs84](http://goo.gl/pEs84)

Rodney

Well i did select something else and as you can see in the 3rd image, its showing my disk as 500gb free space. but i want to keep windows 7. this is where i am facing the problem. Either i have to completely switch to ubuntu or windows. I am unable to create a dual boot system.

---

### Post by Mark Phelps on 2012-02-08
It's good you stopped where you did -- and didn't blindly charge ahead trying to FORCE an installation.  If you had, you would have seriously trashed your system.

From the first image you posted, it looks like you already have the maximum of 4 Primary partitions on your drive.  The installer knows this limit, and since it can't create any more partitions, it does not provide that option.

You have a major problem now because you will end up having to do the following:
1) Figure out which partition to REMOVE
2) Shrink the Win7 OS partition to make some room (Do this ONLY by using the Win7 Disk Management utility)
3) Move your partitions around to push all the free space to the "right" end of the drive (you can do this using the FREE Partition Wizard Boot CD -- which you have to download and burn to CD in MS Windows)
4) Boot into the Ubuntu CD and use the "something else" option to do manual partitioning.

---

### Post by musabhai6012 on 2012-02-08
> **Mark Phelps said:**
> It's good you stopped where you did -- and didn't blindly charge ahead trying to FORCE an installation.  If you had, you would have seriously trashed your system.

From the first image you posted, it looks like you already have the maximum of 4 Primary partitions on your drive.  The installer knows this limit, and since it can't create any more partitions, it does not provide that option.

You have a major problem now because you will end up having to do the following:
1) Figure out which partition to REMOVE
2) Shrink the Win7 OS partition to make some room (Do this ONLY by using the Win7 Disk Management utility)
3) Move your partitions around to push all the free space to the "right" end of the drive (you can do this using the FREE Partition Wizard Boot CD -- which you have to download and burn to CD in MS Windows)
4) Boot into the Ubuntu CD and use the "something else" option to do manual partitioning.

Thanks a lot. problem is solved.

---

