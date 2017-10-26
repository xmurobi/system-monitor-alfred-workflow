# Alfred 2 Top Process Workflow

The initial motive of this workflow is to avoid frequent visits to the Activity Monitor when the fan goes loud. Now it has been evolved with two major features:

- 1) List/Kill Top Processes by Memory/CPU/IO Usage

<img src="https://github.com/singhprd/alfred2-top-workflow/blob/master/screenshots/mixed%20top%20processes.png" height="300">


- 2) Get a glance of system status including internal battery, fan speed, CPU/GPU Temperature, bluetooth battery, disk capacity, etc.

<img src="https://github.com/singhprd/alfred2-top-workflow/blob/master/screenshots/glance.png" height="300">

## Usage

### 0. Show Help 

Just type `-?`, `-h`, or `--help` after the keyword to show help.

<img src="https://github.com/singhprd/alfred2-top-workflow/blob/master/screenshots/help.png" height="300">

### 1. Top Processes

#### A. Keywords:

##### 1.) `top`: Show a mixed processes list based on top cpu/memory usage.


###### 1. `top -m`, `top --memory` to show processes ranked by memory usage

###### 2. `top -c`, `top --cpu`, to show processes ranked by cpu usage

###### 3. `top -i`, `top --io`, to show processes ranked by io usage with **callback** from top io trace collector.

   Top IO requires [DTrace][Dtrace] and it would take a while to finish. The new **callback** design is to run the job in he background and post a notification (OSX 10.8+) using notification center. Click on the notification to show the result in alfred.

![](https://raw.github.com/zhaocai/alfred2-top-workflow/master/screenshots/callback.png) 



###### **Modifier Key**

   - `none`    : The default action is to list files opened by process ID
   - `control` : Kill the selected process
   - `command` : kill forcefully (`kill -9`)
   - `alt`     : Nice (lower) the selected process's cpu priority
   - `shift`   : Search web for process information


##### 2.) `kill`: Filter process to kill.

###### **Modifier Key**

   - `none`: The default action is to kill by process ID
   - `command` : kill forcefully (`kill -9`)

##### 3.) `lsof`: List files opened by process id

###### **Modifier Key**

   - `none`: The default action is to reveal file in Finder

#### B. Filter by Query

##### 1.) Type process name to filter

<img src="https://github.com/singhprd/alfred2-top-workflow/blob/master/screenshots/filtered%20by%20query.png" width="400">

##### 2.) To search for process state, use **:idle**, **:sleep**, **:stopped**, **:zombie**, **:uninterruptible**, **:runnable**, etc.

<img src="https://github.com/singhprd/alfred2-top-workflow/blob/master/screenshots/top_sleep.png" height="300">

### 2. Glance an Eye on your system

#### A. Keywords:

1. `glance`: Show system information including internal battery, bluetooth battery, disk capacity, etc.

<img src="https://github.com/singhprd/alfred2-top-workflow/blob/master/screenshots/battery_2.png" height="300">
#### B. Change Display Order

1. Activate `Alfred Preferences` → `Advanced` → `Top Result Keyword Latching`

    ![](https://raw.github.com/zhaocai/alfred2-top-workflow/master/screenshots/Alfred_Preferences_Learning.png)

2. Hit `Enter` for the feedback item you wish to show up on the top.



## Installation

Two ways are provided:

1. You can download the [Top Processes.alfredworkflow](https://github.com/zhaocai/alfred2-top-workflow/raw/master/Top%20Processes.alfredworkflow) and import to Alfred 2. This method is suitable for **regular users**.

2. You can `git clone` or `fork` this repository and use `rake install` and `rake uninstall` to install. Check `rake -T` for available tasks.
This method create a symlink to the alfred workflow directory: "~/Library/Application Support/Alfred 2/Alfred.alfredpreferences/workflows". This method is suitable for **developers**.


### Forked from Zhao Cai at https://github.com/zhaocai/alfred2-top-workflow
