####################
# set base image (host OS)
#
FROM python:3.8-slim

####################
# Complete installation
# - set the working directory in the container
# - copy the content of the local src directory to the working directory
# - install required Python packages
#
WORKDIR /
COPY src/ .
COPY requirements.txt ./
RUN pip3 install -r /requirements.txt
RUN mkdir nltk_data
RUN python -m nltk.downloader -d ./nltk_data wordnet stopwords
ENV NLTK_DATA=/nltk_data

COPY process_doc.sh .

####################
# Start the app
#
ENTRYPOINT [ "/process_doc.sh" ]
