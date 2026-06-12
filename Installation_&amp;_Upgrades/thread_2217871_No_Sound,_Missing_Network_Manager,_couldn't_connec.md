---
title: "No Sound, Missing Network Manager, couldn't connect to Windows network after clean in"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by kevn57 on 2014-04-18
No Sound ubuntu forums pointed the way to a solution [http://ubuntuforums.org/showthread.php?t=2217635](http://ubuntuforums.org/showthread.php?t=2217635) 1st problem solved


  Missing Network Manager Reddit user genei_ryodan pointed the way to the fix  [http://www.reddit.com/r/Lubuntu/comments/23dhqw/fix_lubuntu_1404_network_manager_missing_from_the/](http://www.reddit.com/r/Lubuntu/comments/23dhqw/fix_lubuntu_1404_network_manager_missing_from_the/)  2nd problem solved



  Samba couldn't connect to windows network
  I fixed this by importing my **/etc/samba/smb.conf** from Lubuntu 13.10

  This line is missing from the samba version I got after installing 14.04
   **name resolve order = lmhosts host wins bcast**


  I follow steps 1-3 on this post and networking works [http://ubuntuforums.org/showthread.php?t=1169149&highlight=win+can%27t+connect+network](http://ubuntuforums.org/showthread.php?t=1169149&highlight=win+can%27t+connect+network)
  Problem 3 solved. I hope this helps somebody else out there

---

