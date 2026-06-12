---
title: "Remove Ubuntu from windows Vista MBR ( Vista Boot screen)"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by R.Wise on 2010-01-15
After searching many forums and googling my fingers off I finally came across something that works and it actually came at Microsoft answers.....Though it is not supported it works!

[FONT=Verdana][FONT=Verdana]1.[FONT=Verdana]Click **Start**, click **All Programs**, and click **Accessories**.[/FONT][/FONT]
 [FONT=Verdana]2.[FONT=Verdana]Right-click **Command Prompt**, and select **Run as Administrator**.[/FONT][/FONT]
 [FONT=Verdana]3.[FONT=Verdana]Click **Continue** or provide Administrator credentials as prompted.[/FONT][/FONT]
 [FONT=Verdana]4.[FONT=Verdana]Type the **bolded text** and press **Enter** after each one.[/FONT][/FONT]
 
 [FONT=Courier New]o*[FONT=Verdana]This command backs up the BCD Store to your Desktop:[/FONT]*[/FONT]
 
 **[FONT=Verdana]BCDEDIT /EXPORT “%HOMEPATH%\DESKTOP\BCDBACKUP”[/FONT]**
 
 [FONT=Courier New]o*[FONT=Verdana]This displays the current entries in the BCD Store. Please find the one pertaining to the OS you want to remove from the Boot menu:[/FONT]*[/FONT]
 
 **[FONT=Verdana]BCDEDIT[/FONT]** 
 
 [FONT=Courier New]o*[FONT=Verdana]This command deletes the entry from the BCD Store. Replace **{[COLOR=#e36c0a]Identifier[/COLOR]}** with the entry you found in the previous step:[/FONT]*[/FONT]
 
 **[FONT=Verdana]BCDEDIT /DELETE {[COLOR=#e36c0a]Identifier[/COLOR]} /F[/FONT]** 
 
 [FONT=Verdana]5.[FONT=Verdana]Now restart the computer and the boot entry should be successfully removed from the system.[/FONT][/FONT]


[FONT=Verdana][FONT=Verdana]Do this exactly as it says and Ubuntu is gone from your boot up options.[/FONT][/FONT]


[FONT=Verdana][FONT=Verdana]I installed Wubi in my "D" drive and when I used the uninstall it worked but left this option behind and I wrestled a long while to find this and it worked. Now I know how to use Unbuntu it is going on my old laptop.:o
[/FONT][/FONT]
[/FONT]

---

