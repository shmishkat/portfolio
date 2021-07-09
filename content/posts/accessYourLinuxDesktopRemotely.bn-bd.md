+++
author = "Sarowar Hossain Mishkat"
title = "Access Your Linux Desktop Remotely"
date = "2021-07-09"
description = "Using my old computer as a media server and seedbox"
tags = [
    "Linux",
    "Kubuntu",
    "Krfb",
    "Remote Acess",
    "KWallet",
    "VNC",
    "MacOS",
    "qBittorrent",
    "Plex",
    "KDE Plasma"
]
+++

I was contemplating a project like a media server, torrent seedbox, or simply backup files via P2P(i. e. Resilio Sync) using a Raspberry Pi 4. Then I realized I have an 11-12 y/o desktop PC in my room that I can use for the project. Well, this PC will draw way more electricity than a Raspberry Pi would but I wanted to test it then I’ll consider building such a system. 

#### Here are the requirements and objectives: ####
- Using Linux desktop remotely on any device (GUI).
- Only powering on the Linux desktop should work. (No tasks on the Linux desktop rather plug and play).
- Direct access remotely without providing any password on Linux desktop i. e. User login, remote desktop server because I want to use the Linux desktop without a monitor.
- Lightweight remote access server app for the Linux desktop since it’s an old machine.

#### PC Configuration: ####

![PC Config](/images/accessLinuxRemotely/pcconfig.png "PC Config")

So Let’s Begin!
First of all, the 4GB stick along with the slot got burnt so I had to work with 2GB ram only, hence I needed a lightweight Linux distro. I chose Kubuntu 20.04 LTS which came with KDE Plasma 5 desktop environment.

I used the [Krfb](https://github.com/KDE/krfb "Krfb's GitHub Repository") desktop sharing application developed by [KDE](https://kde.org/ "KDE Website") which is open-source and lightweight.

To install Krfb on your Linux system, open up the terminal (Konsole on Kubuntu) and run these commands. 

>sudo apt-get update

>sudo apt install krdc


Since one of my requirements was that I didn’t want to configure anything on the Linux system every time I rebooted it. So, I had to enable automatic login. </br>
***Click on the Application Launcher>Click on your profile>Select automatic login.***

Then I needed to make sure Krfb was started automatically at login.</br>
***Click on Application Launcher>Search Autostart and open the application>Click on app program>Search “Krfb” and add it to the list.***</br> 

I also added qBittorent and Plex Media Server to the list because I wanted to access the qBittorent and Plex Media Server Web UI. 

#### Now open up Krfb and you should see something like this:

![Krfb](/images/accessLinuxRemotely/krfb.png "Krfb")


Check **Enable Desktop Sharing** and then you should be able to see your Linux desktop’s IP address which we will use to access this desktop remotely. Then set a strong password. You will see another field named **Unattended Access**, which was very important in my case.
So **Unattended Access** is basically if someone has the password and IP address of your machine s/he will be able to access your machine anytime and as many times as they want without any confirmation from you. Unattended access was the way to go for me since I didn’t want to give permission every time I tried to access the desktop. I recommend keeping both of the passwords the same. 

On Kubuntu, **Kwallet** handles the passwords so every time you reboot your Linux system Kwallet pops up and asks for the password for Krfb. If you turn off Kwallent completely Krfb won’t remember its password so let’s ***search KDE Wallet in the application launcher and open KDE Wallet and select “Close when the last application stops using it.”***

Now go to the device where you want to access the Linux desktop remotely. 
You can use any VNC Client application like **VNC Viewer** by **RealVNC** or if you have any built-in one. In my case, I wanted to access it on my MacBook Pro which had a built-in VNC Viewer named **"Screen Sharing"**. ***Open up the VNC Client you have and type the IP address that we found on Krfb, like this "VNC://(IP address of the Linux desktop)". It will prompt for the password, type it and press enter.***

#### Voilà! Now you have remote access to the Linux desktop.

![Remote access of the Linux desktop on MacBook Pro](/images/accessLinuxRemotely/remoteaccess.png "Remote access of the Linux desktop on MacBook Pro")

#### Extras: 
I used qBittorrent to download torrents and Plex Media Server for my media server. Luckily both had Web UIs, hence I could access both of them from my web browser and all the other tasks could be done using remote access. 

**Thanks for reading!**</br>
Hopefully next time I’ll post on how to use SSH to access remote Linux devices which will be more straightforward.

Feel free to email me if you have any queries. 
