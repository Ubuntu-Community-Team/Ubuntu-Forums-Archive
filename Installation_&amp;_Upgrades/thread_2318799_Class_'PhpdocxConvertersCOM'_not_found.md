---
title: "Class 'Phpdocx\Converters\COM' not found"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by Gurwinder_waraich on 2016-03-29
Hi,
I am using Ubuntu 14.04 LTS and i was installing phpdocx to convert docx to pdf, all was going well. I was able generate docx and pdf too but unfortunately got stuck in generating using **"transformDocxUsingMSWord"** and when i tried to run php file to generate docx or pdf in **"transformDocxUsingMSWord" **it gives error 

**PHP Fatal error:  Class 'Phpdocx\Converters\COM' not found in /var/www/phpdocx-corporate-5.5-ns/Classes/Phpdocx/Converters/MSWordInterface.inc on line 52**

I thought this is regarding php extension but i found nothing while googling for long time. However, it shows method to enable "**com"** extension in windows. So, basically i found nothing to overcome this problem

I'm here to look for solution, maybe someone help me with issue.

---

### Post by SeijiSensei on 2016-03-29
So did you look at that file and line 52?  Is there a class defined anywhere in the PHP code with that name?  Any chance this only works with PHP on a Windows machine?

---

### Post by Gurwinder_waraich on 2016-03-29
Thanks for reply,

Yes i looked on that 52 line, Here it is:
**//Lets start a Word instance**
[B]        $MSWordInstance = new COM("word.application") or exit('A working copy of Word was not found on this server');

[/B]This can start a word instance, but here it is unable to start an instance. It throws an error:
[B]
PHP Fatal error:  Class 'Phpdocx\Converters\COM' not found in /var/www/phpdocx-corporate-5.5-ns/Classes/Phpdocx/Converters/MSWordInterface.inc on line 52

[/B]
In windows i was able to en[FONT=arial black][FONT=arial][/FONT][/FONT]able this com extension by **"extension=php_com_dotnet.dll" **and the whole thing was working good[B]

[/B]But in "ubuntu" i did not get anything to enable this COM extension (COM with php)[B]
[/B]
[FONT=arial][/FONT]

---

### Post by SeijiSensei on 2016-03-29
I'd suggest you stick with Windows.  Using "apt-cache search php | grep dotnet" unsurprisingly finds no equivalent entries.  Technologies like .NET are proprietary to Windows systems and typically have no Linux equivalents.

---

### Post by Gurwinder_waraich on 2016-03-30
But i need to use this for Linux server. So, if this does not work on Linux do we have any other option to be used in its place. Please do tell me if i can use other method to overcome this problem.
Thanks again !!

---

### Post by SeijiSensei on 2016-03-30
I doubt there are any good solutions.  You could try installing WINE and trying to run the Windows Apache server on that.  Otherwise you could install a virtualization solution like VirtualBox and run Windows in a virtual machine on top of Linux.  But I don't think you'll find any native Linux solution for your task.

Have you asked for help from the people who made the phpdocx package?  That's probably your best bet.

---

### Post by Gurwinder_waraich on 2016-03-31
Yes, i asked phpdocx support team they are also saying that "[COLOR=#666666][FONT=Open Sans]PHP COM extension is only available for Windows servers" but hey are providing conversion plugin for Linux that nearly solved my problem but still it's not generating pdf correctly.
Anyway **thanks** for your time and support.
Here is a link to conversion plugin for PHPdocx:
[/FONT][/COLOR][http://www.phpdocx.com/documentation/conversion-plugin](http://www.phpdocx.com/documentation/conversion-plugin)

Maybe this can help someone else.

---

