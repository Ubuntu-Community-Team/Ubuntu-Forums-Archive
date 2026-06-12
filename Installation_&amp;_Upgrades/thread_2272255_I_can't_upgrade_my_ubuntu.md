---
title: "I can't upgrade my ubuntu"
date: 2015-04-05
forum: Installation &amp; Upgrades
---

### Post by Jonatan Formentera on 2015-04-05
Hi, I have a problem. I was upgrading my notebook with ubuntu 14.04 when I interrupted the download by mistake.Now, it says to me 'Error:BrokenCount>0'. On the left top appears the prohibited direction signal. It also says to me "I can't download the package installation- I think I need the flash plugging installer but i lost my Internet connection and can't connect the computer to the web
Can anyone help me?
Thanks

---

### Post by ian-weisser on 2015-04-05
> **Jonatan Formentera said:**
> I was upgrading my notebook with ubuntu 14.04 when I interrupted the download

Open a terminal.
Try:
```
sudo apt-get update
sudo apt-get upgrade
```

And paste the complete output (it may be long) here. Use [CODE] tags for the output.

---

### Post by grahammechanical on 2015-04-05
> I think I need the flash plugging installer

The flash plugin installer is there to install a flash plugin so that the web browser can render web sites that use flash content. Once the plugin is downloaded and installed the plugin installer is not involved in rendering web sites

Furthermore, the failure to render flash content is not connected to a failure to update/upgrade Ubuntu or connect to the internet.

Is the "broken count" error connected to the lost internet connection? Please run

```
sudo apt-get update
sudo apt-get upgrade
```

And post any error messages. Enclosed them in QUOTE tags. Please confirm that the router is connected to the ISP and Network Manager is saying that Ubuntu is connected to the router, either as a Wired or a WiFi connection.

Regards.

---

### Post by Jonatan Formentera on 2015-04-05
I don't know what you mean by  "paste the complete output (it may be long) here. Use [CODE] tags for the output". I'm on the terminal and have a long list of situations whcich begin with a letter i a lower case. Are the tags you mean? I don't know how to use them

---

### Post by flaymond on 2015-04-05
[QUOTE=Jonatan Formentera]I don't know what you mean by  "paste the complete output (it may be long) here. Use ```
 tags for the output". I'm on the terminal and have a long list of situations whcich begin with a letter i a lower case. Are the tags you mean? I don't know how to use them[/QUOTE]

[CODE], >  is a BB code tags to formatting the structure of the text, to be more manageable and pretty.

Example for [QUOTE] tag :

[noparse][QUOTE] Hello World! [/noparse]

> Hello World!


^
This is Quote structure, it's make a text like in a quote.

Example for [CODE] tag:

[noparse][CODE] Hello World! 
```[/noparse]


```
 Hello World! 
```

^ This is code structure, to increase readibility of codes especially bash (a common shell for Linux today)

You can read more about Ubuntu Forums BB code - [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)


@ Bapoumba, thanks for mentioning the [noparse] tag. It help me a lot and decreasing confusion. :KS

---

### Post by ajgreeny on 2015-04-05
See Code-Tags in my signature for a how-to.

To copy the terminal output highlight all with the mouse as you would normally (Ctrl+A will not work in terminal) then right click and Copy. you can then paste in the usual way but using code tags.

---

### Post by bapoumba on 2015-04-05
@InterProg : have a look at the noparse tag :tongue:

---

### Post by Jonatan Formentera on 2015-04-05
Thank you. I was trying doing it with  Control + v but I couldn't. I could paste it according to your method and now I waiting for the results

---

