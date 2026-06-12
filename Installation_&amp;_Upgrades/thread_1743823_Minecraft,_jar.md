---
title: "Minecraft, jar"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by automattig on 2011-04-29
I'm playing minecraft and I am getting annoyed that I have to run the command java -jar minecraft.jar every time I want to run it.  Is there a way to create a simple icon launcher, and if possible how do I create it?

Regards

---

### Post by greybirds on 2011-05-01
Yeah, there is. I'm assuming you're using Ubuntu, and not Kubuntu or some other variant. It's possible there as well, but I just don't know offhand how to do it. I'm also assuming you're not using Unity; if you are, I'm afraid I can't help you.

You have two quick/dirty choices: you can add Minecraft to your Games menu or create a launcher in the panel for it. 

To add it to your menu:
[LIST=1]
[*]Right click the Applications menu and select "Edit Menu".
[*]Click the "Games" section, then click the "New Item" button. A launcher properties window opens.
[*]Follow the instructions under Common Steps, below.
[/LIST]

To add a launcher to the panel:
[LIST=1]
[*]Right click the panel and select "Add to panel..."
[*]Select "Custom Application Launcher", then click the Add button.
[*]A launcher properties window opens.
[*]Follow the instructions under Common Steps, below.
[/LIST]

Common Steps:
[LIST=1]
[*]Leave type as application and fill in the name with "Minecraft".
[*]Click the "Browse" button, navigate to the folder where you store your minecraft.jar and select it, then click Open.
[*]Notice it filled the "Command" text box with the path to your minecraft.jar; add "java -jar " (without quotes, but with the space at the end) to the beginning of this text, so it looks like this: **java -jar /home/your_username/some/folders/minecraft.jar**.
[*]Click the icon in the upper-left hand corner and pick a custom icon if you want. You can download pretty much any image from the web; Google Images has lots of good options.
[*]Close the launcher properties window and the menu editor if it's open. Minecraft should be waiting for you in Applications -> Games or on your panel.
[/LIST]

---

