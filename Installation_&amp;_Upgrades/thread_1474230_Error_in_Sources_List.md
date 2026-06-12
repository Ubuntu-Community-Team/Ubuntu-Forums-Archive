---
title: "Error in Sources List"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Mutiechameleon on 2010-05-05
I'm having some trouble with Synaptic and it led me to now know that there's an error in my sources list. 

I did this: 
cat /etc/apt/sources.list.d/medibuntu.list

I got this: 
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<noscript>
<meta http-equiv="refresh" content="0;url=http://finder.cox.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=96e687opkbv4scrood8k84drs6gw5duf&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fmedibuntu.sos-sts.com%2Fsources.list.d%2Ffeisty.list&AddInType=4&Version=2.1.1-1.62base&Referer=&Implementation=0"/>
</noscript>
<script type="text/javascript">
window.location.replace("http://finder.cox.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=96e687opkbv4scrood8k84drs6gw5duf&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fmedibuntu.sos-sts.com%2Fsources.list.d%2Ffeisty.list&AddInType=4&Version=2.1.1-1.62base&Referer=&Implementation=0");
</script>
</head>
<body>
</body>
</html>

Any help would be greatly appreciated, meanwhile I'm working around it by working on windows for what I needed instead.

---

### Post by plucky on 2010-05-06
Your **medibuntu.list** file is corrupt.

To remove it using a terminal window,use ```
sudo rm /etc/apt/sources.list.d/medibuntu.*
``` 
Be careful using the sudo rm command as there is no going back.


Then go to link to add the [Medibuntu Repository](https://help.ubuntu.com/community/Medibuntu)

Good Luck

---

### Post by Mutiechameleon on 2010-05-06
Thanks for your help. Everything seems to be back to normal now.

---

