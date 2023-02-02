# islandora_workbench_demo_content
Demo content to work with [islandora_workbench](https://github.com/mjordan/islandora_workbench)

1. Clone https://github.com/mjordan/islandora_workbench
1. Clone this repo into the islandora_workbench directory (`cd islandora_workbench && git clone https://github.com/DonRichards/islandora_workbench_demo_content`)
1. Open example_content.yml and change the line with "nopassword" to the password or to contents of isle-dc/secrets/live/DRUPAL_DEFAULT_ACCOUNT_PASSWORD
1. Open example_content.yml and change the line with input directory to include the absolute path for demo_content_files/ when embedded inside of the container. `input_dir: /workbench/islandora_workbench_demo_content/demo_content_files`
1. Then run the docker build from parent directory islandora_workbench: `docker build -t workbench-docker .`
1. Check the config `docker run -it --rm --network="host" -v $(pwd):/workbench --name my-running-workbench workbench-docker bash -lc "cd /workbench ; python setup.py install ; ./workbench --config /workbench/islandora_workbench_demo_content/example_content.yml --check"`
1. Then run the newly created container `docker run -it --rm --network="host" -v $(pwd):/workbench --name my-running-workbench workbench-docker bash -lc "cd /workbench ; python setup.py install ; ./workbench --config /workbench/islandora_workbench_demo_content/example_content.yml"`

... ROLLBACK IS CURRENTLY NOT WORKING WITH THIS DEMO CONTENT ...
## To rollback the demo content
1. Check the config `docker run -it --rm --network="host" -v $(pwd):/workbench --name my-running-workbench workbench-docker bash -lc "cd /workbench ; python setup.py install ; ./workbench --config /workbench/rollback.yml"`