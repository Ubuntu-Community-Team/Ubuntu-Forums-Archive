---
title: "Laser Brother HL-L2390DW printer won't print with Ubuntu 20.04.6 LTS"
date: 2023-10-15
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2023-10-15
Just changed Internet provider. Setup Brother printer hard wired and setup printer wi-fi settings to new network to get all connected. Have a solid green light showing wi-fi setting is good. However can't get printer to print anything now. Worked fine with prior Internet provider.

Help please?

---

### Post by makitso on 2023-10-15
> **cybrsaylr said:**
> Just changed Internet provider. Setup Brother printer hard wired and setup printer wi-fi settings to new network to get all connected. Have a solid green light showing wi-fi setting is good. However can't get printer to print anything now. Worked fine with prior Internet provider.

Help please?
I am a little confused by your post.  
[LIST]
[*]Changing ISPs should not impact your local printer unless you also changed out your LAN system at the same time, e.g. ISPs modem providing Wifi.
[*]Are you running 20.04.06 or 22.04 as your signature block states?
[*]Assuming your Brother printer is using WiFi then:
[LIST]
[*]Do you see your printer is the Control Center?  if not you may need to reinstall the printer.
[/LIST]
[/LIST]

---

### Post by iamjiwjr on 2023-10-15
I hope something in my experience can help here. I have this printer. Mine does not work consistently with the driverless printing setup that is the default. So I deleted those packages, ipp-usb and sane-airscan. Then I installed the deb of the scanner driver (brscan4) from the Brother site. The printer driver (printer-driver-brlaser) is pre-installed from the Ubuntu repo and is already present. Then I added the printer through settings, then rebooted. Printer and scanner work great.

---

### Post by send2 on 2023-10-15
Generally, I have found that going to the Brother printer website and downloading the drivers for your printer and installing from there results in a printer working. I have a Brother printer and installed the drivers following the instructions on the Brother printer website that corresponds to my printer model.

1. Go to the Brother website and enter your printer model
2. Download all drivers that relate to your printer. There should be a general installer file. You will use that to install all required drivers
3. After downloading the drivers extract the installer and all necessary drivers as per instructions from Brother website
4. Follow the instructions in terminal to install the installer and then it will instruct you on how to proceed in terminal. For me you will get to the question in terminal "Will you specify the Device URI?" answer yes and then choose number 11 from list to use your IP address to install drivers. Don't forger to choose yes when you are asked if you want to print a test page. That worked for me. 

I have a Brother MFC-L8600CDW laser printer and it works good. Good luck. 

Let me see if I can bring up your model on the Brother printer webpage:

[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2390dw_us&_gl=1*f16uno*_ga*mjy1otqymzm3lje2otcznzc4mze.*_ga_ncew43sj8w*mty5nzm3nzgzmc4xljeumty5nzm3nzg2os4yms4wlja.*_gcl_au*otyzmdu2mja5lje2otcznzc4mze.&_ga=2.152934521.1516919153.1697377832-265942337.1697377831&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2390dw_us&_gl=1*f16uno*_ga*mjy1otqymzm3lje2otcznzc4mze.*_ga_ncew43sj8w*mty5nzm3nzgzmc4xljeumty5nzm3nzg2os4yms4wlja.*_gcl_au*otyzmdu2mja5lje2otcznzc4mze.&_ga=2.152934521.1516919153.1697377832-265942337.1697377831&os=128)


You should have the following files to download: Driver Install Tool, Linux Printer Driver, Scanner Driver. Don't forget to select Linux (deb) package corresponding to your system and pay close attention on the install instruction that will come up when you choose a driver to download it. What I did was take a screen shot of each drive installation instructions to refer back to as I was installing the drivers. Hope this helps you.

---

### Post by cybrsaylr on 2023-10-15
Am running 20.04.06 now.
Had trouble with 22.04 that I could not correct so went back to 20.04 which runs fine. Plan to upgrade to 24.04 when it is released ... if reviews on it are positive.

All I can say is WOW. Installing this Laser Brother printer is a PAIN compared to other printer installs done in the past!

Thanks for all your help guys. This install was far more difficult than expected but it was done. Had to repeat install a few times due to putting in an incorrect character of misplaced . or - at times. 

Even used this nice YouTube clip for assistance: [https://www.youtube.com/watch?v=T4nR1253wx8](https://www.youtube.com/watch?v=T4nR1253wx8)

---

### Post by oldfred on 2023-10-15
I have same printer and have not had those issues.

I did install it while still using Focal. If I remember correctly I did have a bit of an issue with getting scanner to work. Once I had both USB & Internet connected then it worked.
I never installed any drivers directly from Brother.

With Jammy only issue is that I see 3 printers and only one really works.
With Mantic, I only get one printer installed. Have not fully tested that yet. Still using Jammy as main working install.

---

### Post by cybrsaylr on 2023-10-16
Printer seems to work well now with Focal. Haven't tried out scanner yet. Hope scanner works. It always made copies of anything desired with no issues.

With Focal I also see 3 printers with the middle one in that group highlighted and assume it's the working one.
Is it safe to delete the other 2 printers listed in, settings > printers ?

Was wondering when I upgrade to Ubuntu 24.04 LTS, will it be necessary to go through this same install process all over again?

---

