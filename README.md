# evcc-hassio-addon
evcc Add-on for Home Assistant OS

# Installation

Follow these steps to get the add-on installed on your system:

  - Navigate in your Home Assistant frontend to Supervisor -> Add-on Store.
  
    <img width="500" src="docs/addonstore.png">
  
  - Click -> Add-on Store.
  
    <img width="200" src="docs/addonstore2.png">
  
  - Click -> three dots -> Repositories.
   
    <img width="400" src="docs/addonstore3.png">
  
  - Click -> three dots -> Repositories.
  
    <img width="400" src="docs/addonstore4.png">
  
  - Copy "https://github.com/evcc-io/hassio-addon" Click -> Add
  
  - Reload the WebSite (CTRL+R or CTRL+F5 or CTRL+Fn+F5)
  - Find the "evcc" add-on and click it.
  - Click on the "INSTALL" button.
  - Go to Information nenu in the "evcc" Addon and activate "show in side bar"
    (evcc UI  `http://your-ha-instance-ip-address:7070`)
  - Go to Configuration menu and select your working directory (example):
  
    <img width="100" src="docs/addonstore5.png">

        - config_file: /config/evcc.yaml
        - sqlite_file: /data/evcc.db

Alternative file location:

        - config_file: /config/evcc/evcc.yaml
        - sqlite_file: /config/evcc/evcc.db
 You have to copy the /data/evcc.db to /config/evcc !
    
  - evcc configuration file evcc.yaml
      - Copy https://github.com/evcc-io/evcc/blob/master/evcc.dist.yaml to your homeassistant/config/ directory
      - Rename  evcc.dist.yaml to evcc.yaml (note: configure first to your needs the evcc.yaml or use a working configuration)
        
        Location of "config" directroy in HA:
        - https://www.home-assistant.io/docs/configuration/
        - https://www.home-assistant.io/common-tasks/os/#installing-and-using-the-samba-add-on

# !! NOTE !!

The Home Assistant Addon evcc is based on docker, there is no possibility to create a configuration file for evcc inside the evcc docker with "evcc configure"!

As a result of this a working evcc configuration is required. 

To do this, perform the steps in the documentation of evcc to create a configuration file "evcc.yaml":

  - https://docs.evcc.io/docs/installation/manual


# Configuration of [evcc](https://github.com/evcc-io/evcc)

   - https://docs.evcc.io/docs/guides/setup

# How to find and copy /data/evcc.db

Create a folder e.g. /evcc in homeassitant config directory (/homeassistant or /config).

Install "Advanced SSH & Web Terminal" (Advanced Version!!!)
- switch off "secure mode"
- restart addon
- start UI


      docker -ps a

save the CONTAINER ID of evcc/evcc:0.130.12  -> e.g. 6d0b4119b012 (CONTAINER ID of EVCC)

List the files in /data:

     docker exec 6d0b4119b012 ls -la /data

you will find your evcc.db

Copy your evcc to /config/evcc:

     docker cp 6d0b4119b012:/data/evcc.db /homeassistant/evcc/

