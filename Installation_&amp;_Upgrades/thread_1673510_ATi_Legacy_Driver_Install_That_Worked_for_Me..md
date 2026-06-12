---
title: "ATi Legacy Driver Install That Worked for Me."
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Tejekion on 2011-01-22
I want to first thank not only the Ubuntu team, but the ENTIRE Linux community for offering such robust alternatives to the Dictatorial Operating Systems out there like MS Windows, and Mac OS X, that require you to buy their software and/or hardware in order for you to use it. I also would like to personally thank the Wine team for their great efforts of bringing DirectX playability to the Linux community. For without them, a lot of poor people like me had to make the decision to either unlawfully use those dictatorial OSs to play their favorite games, or morally not play them, and stick with what games could found on Linux. You see I'm not much of a gamer. Its just that the games I happen to like(Shaiya, FlyFF, Pangya, etc.) Are generally the "Free to Play" MMORPGs that until the Wine community advanced Wine so much that I can finally play them on Linux, thus giving me the third alternative I've waited years for. To be able to morally play those "Free to Play" games on literally "Free to Have" OSs. This has actually helped me alot spirutually as I try to clean up my act, and get right with God(Please no flames here as I believe that the Linux community as made a way for even poor people like me to have all the choices if the proprietary OSs without having to steal them. God bless you all for that).

It was my appreciation for that Morality that led me to take the few minutes to register here. So that I could help any one who may have been having the same problem getting at least legacy ATi drivers to install on legacy hardware(I have a Radeon Mobility 9000 PCI graphics card).

I consider myself to be very green when it comes to Linux as I have installed and used Linux ocassionally over the last 10 years, trying several distros, like Kubuntu the best out of all of them, but one thing would make me go back to Windows, the lack of ports of the games I liked to play for Windows, to Linux. With no way to play them on Linux I'd have to go back to Windows. This also limited the kind of hardware I could use. I generally would have to buy a Dell or HP that either a coupla generations behind what's current, buy and rebuild something that was broken, or both. 

At any rate what I did was very simple. Kind of a brute force method. I was watching a "How To" video on YouTube and noticed the guy was using Synaptic Package Manager,which I didn't have. It took me 5 days to figure out how to download it as I didn't know the package name(I quickly found the sudo apt-get install command on the internet). Once I installed it I tried the methods the video suggested, but really didn't understand what he was saying. So I simply loaded every ATi non debug driver that Synaptic found. I rebooted and noticed that my desktop popped up instantly, signalling that at least 2D drivers were installed. Whenever I tried to look at the OpenGL drivers, KInfoCenter would crash. I then removed the newest version of the ATi drivers and rebooted and voila! I check KInfo Center again and OpenGL Reported my Video Card, and driver version.

I have played two versions of Tux Racer and Armagettron without any problems.

Sorry for the long drawn out explanation, but I really think that the Linux community needs to point out the morally and spiritually uplifting aspects of their work also. Many people that use computers call themselves Christian, Islamic, or whatever religion they may worship God under. And none of those religions say anything good about stealing. Linux OS gives even the most economically challenged individuals the chance to stay morally clean, even if it requires what most consider a very hard change from their "point, click and install" OS that they are used to.

---

