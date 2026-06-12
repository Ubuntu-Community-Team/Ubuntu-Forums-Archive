---
title: "Installing enlightenment 17 in lucid"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by garfonkee on 2011-01-22
How do I go about this? Which repository have enlightenment 17? There only seems to be e16..

---

### Post by JOHNNYG713 on 2011-01-22
See this [http://www.google.com/url?sa=t&source=web&cd=5&ved=0CDEQFjAE&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1483298&rct=j&q=how%20to%20install%20enlightenment%20in%20lucid&ei=ocY6TZKVOITdgQfY6bzTCA&usg=AFQjCNE6X_Zlo4sFObR73tgDpL1YdBv5-A&cad=rja](http://www.google.com/url?sa=t&source=web&cd=5&ved=0CDEQFjAE&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1483298&rct=j&q=how%20to%20install%20enlightenment%20in%20lucid&ei=ocY6TZKVOITdgQfY6bzTCA&usg=AFQjCNE6X_Zlo4sFObR73tgDpL1YdBv5-A&cad=rja)

Here is the repo

deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) *lucid* main extras


Add the key

sudo apt-key add repo.key
 [FONT=Sans]or[/FONT]
 su root
apt-key add repo.key

Then ```
sudo apt-get update
``````
sudo apt-get install enlightenment
```

---

### Post by Frogs Hair on 2011-01-22
E17 is in the Synaptic Package Manager on 10.10 , but I'm not sure about 10.04 .

---

