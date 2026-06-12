---
title: "php problem after updating to Ubuntu 21.10"
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by townhill on 2021-10-19
I just updated from 21.04 t0 21.10 and in the process now have php 8.0.8 installed.  My problem is that local php code no longer works on my local web pages. It's not that the php code displays as text, the problem is that nothing displays at all.  The strange part is that on one page I have php script that uses file_get_contents to pull in a json file from openweathermap.org and display fields from that json file and that works fine, but later on the page i run the same script on a local json file that stores my bookmarks and that script displays nothing.  

i'm assuming the problem is coming as a result of the upgrade to 21.10.  Any thought on what i can do to fix this?

Thanks,

Bob

---

### Post by TheFu on 2021-10-19
Have you looked at the webapp log files?
What about the web server logs?
Anything in either of those that gives a hint for the root problem?

Port the php code from the php version it used before to the new php version on 21.10?
Don't forget to check any external modules or missing modules that no longer exist.

Or you can move the old php stuff into a container running the OS you need. This wouldn't require porting immediately.  LXD containers are almost like full VMs, so you can consider them that for porting code.  Just be aware that certain things that need root to work often won't in a container without breaking the container security model of using unprivileged users.  Things like NFS or iptables or VPNs are what I've seen have issues with LXD containers. Of course, those can be run on the base OS to do what you need, probably.

The command to see the available images from the lxd repo is:
```
$ lxc image list images:ubuntu/21.04
```

There is a downside. LXD is only available as a snap package.  Snaps get updated without our permission. If you are avoiding snaps, well. There's that.  I've had to fall back to a prior version of the lxd snap when it broke my LXD host. That happened once. But I've not seen any other negative.  Ubuntu LXD images are bloated, but not as bloated as some like CentOS which is 2x larger. OTOH, you can use an alpine image which I think is 4MB, but pretty bare bones.

Anyway, you have some options.  There are others - like using a docker container instead of lxd.  Up to you.

Porting the php code is something that will need to happen. So either you do it or put a team of devs on it or if it is an external tool, perhaps delaying until that other team moves their software to v8 of php is advised?
In the last few months, I've had to split a few php webapps apart that used to run on the same VM host due to php dependency differences.  I'll probably convert the last one to an lxd container this month, since the program release I'm on now loses support in a few weeks. Yes, it is a hassle. Plus this webapp has lots of data, which generally isn't great for containers. I can pass through some storage to the LXD container using lxd commands. No need for NFS, which is good. [Https://askubuntu.com/questions/691039/adding-a-shared-host-directory-to-an-lxc-lxd-container](Https://askubuntu.com/questions/691039/adding-a-shared-host-directory-to-an-lxc-lxd-container)

---

### Post by townhill on 2021-10-20
Thanks for the reply.  i'm just a hobbyist writing code on my local machine to learn more about how things work.  As far as I have gotten with docker is an nginx installation on one of my laptops but this machine is runnning Apache and I just want a working php environment to play in.   Im thinking maybe to roll back to a previous version of php but I would rather keep using version 8 and figure out how to fix the problem. I took a look at the server log and it seems there is a server error 500 happening when loading local files, but only for certain php operations.  I tried a fresh install of version 8, but no joy.

Setting up a simple phpinfo() page in a local directory in /var/www/html/ works fine, the page displays the php info without a problem and the Apache2 server log is showing a status code 200.  Any other page in the same directory will display the json data from a remote source but not the local source and the log shows a 500 status code for the page.  

For instance on a page, this code works fine. Pulling data from a remote json file  the remote weather data displays without a problem:
 
```

<?php
 $jsonfile = file_get_contents("http://api.openweathermap.org/data/2.5/weather?q=someplace&units=imperial&appid=myid");
 $jsondata = json_decode($jsonfile);
 $temp = $jsondata->main->temp;
 $pressure = $jsondata->main->pressure;
 $mintemp = $jsondata->main->temp_min;
 $maxtemp = $jsondata->main->temp_max;
 $wind = $jsondata->wind->speed;
 $humidity = $jsondata->main->humidity;
 $desc = $jsondata->weather[0]->description;                                                            
 $maind = $jsondata->weather[0]->main;                                                                  
 $ico = $jsondata->weather[0]->icon;                                                                    
 echo "<p><img class='weatherpic' src='http://openweathermap.org/img/w/" . $ico . ".png" .  "'>" . "Temperature: " . $temp . " F" . "<br>" .  "Weather Conditions: " . $desc . "<br>" . " Humidity: " . $humidi    ty . "%" . " - " .  "Wind Speed: " . round(($wind*2.236),2) . " mph" . "</p>";                         
  ?>
```

but this code, pulling info from a local json file shows nothing.  The heading "Category 1" is echoed just fine but no json data is displayed

  ```

<?php                                                                                           
  $json = file_get_contents("homepage.json");                                                  
  $json_data = json_decode($json,true);                                                        
 ?>                                                                                              
                                                                               
 <?php
    echo "<h1>Category 1</h1>"; 
 ?>
 
 <?php
 foreach ($json_data as $thefile)
 {if ($thefile[category] == 'Category 1') 
 echo  "<li><a href='" . $thefile[url]  . "'" . "target='_blank'>" . $thefile[name] . "</a>" . "</li>"; }
 ?>

```

So I think the json extension is working ok because i can use it to decode a file from a remote site.  This maybe leaves some server configuration problem where Apache has a problem with php code in any file in the /var/www/html/ directory? Dunno.  Even pages that are not decoding json don't work.  Probably not an Ubuntu upgrade problem unless I did something stupid during the upgrade process.

---

### Post by SeijiSensei on 2021-10-20
You need to include complete paths in functions like file_get_contents().  The default path is probably "/var/www/html" but don't rely on that. Specify the complete path to your file in the function.

---

### Post by townhill on 2021-10-20
Thanks for the reply.  I have tried the absolute path which, as you say, is indeed /var/www/html/subdirectory/myjson.file but that is not working either.  The more I look into it the more I think it is a php or Apache problem and only tangentially related to the Ubuntu upgrade, especially because the problems are not solely related to file_get_contents.  As much a I very much appreciate and rely on the help available on Ubuntu Forums (which led me to immediately post here when I had a problem) I think it might be more appropriate to continue going through the code to try and find the problem and also to check PHP and Apache related forums for clues and let the moderators on this forum do what they do best which is sorting out Ubuntu issues.  

That being said I should probably close this thread even though it is not technically 'solved' ?
[h=1][/h]

---

### Post by townhill on 2021-10-20
So it is a PHP issue, at least for the json problem.  PHP 7.4 (the way i had it configured anyway) did not require the name of a name/value pair to be quoted and I developed a habit of writing it as above but version 8 does not tolerate this.  Changing 
```
{if ($thefile[category] == 'Category 1')
``` to 
```
{if ($thefile['category'] == 'Category 1')
```
did the trick.  

I'm sure that going over other code that currently has problems will reveal the same sort of thing.  I think PHP has wanted quoted name values for a long time and this shows me the importance of reading the spec.  :redface:

Thanks to TheFu  and SeijiSensei for their help.

---

