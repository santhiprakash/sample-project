# Base image - using LTS version instead of 22 for stability
FROM node:22-slim

# Install essential tools and dependencies with proper formatting
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    procps \
    sudo \
    less \
    vim \
    # Clean up apt cache to reduce image size
    && rm -rf /var/lib/apt/lists/*

# Create app directory and set permissions
WORKDIR /workspace
RUN chown node:node /workspace

# Install stable npm version
RUN npm install -g npm@latest

# Configure sudo access for node user
RUN echo "node ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/node \
    && chmod 0440 /etc/sudoers.d/node

# Switch to non-root user
USER node

# Set environment variables
ENV NODE_ENV=development

# Volume configuration
VOLUME [ "/workspace" ]